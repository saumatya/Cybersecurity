Page / Feature                | Guest        | Reserver         | Administrator
-----------------------------|--------------|------------------|---------------------
/ (index)                    | ✅           | ✅               | ✅
└─ View resource form        | ❌           | ✅               | ✅ *note added
└─ Create new resource       | ❌ *1        | ❌ *2            | ✅ *3
/login                       | ✅           | ✅               | ✅
└─ Register new account      | ✅ *4        | ✅ *4            | ✅ *4
└─ Email validation          | ✅ *5        | ✅ *5            | ✅ *5
└─ Password validation       | ✅ *6        | ✅ *6            | ✅ *6
└─ Age restriction (15+)     | ✅ *14       | ✅ *14           | ✅ *14
└─ Login with wrong creds    | ❌ *7        | ❌ *7            | ❌ *7
/reservation                 | ❌ *8        | ✅               | ✅
└─ View all reservations     | ❌ *15       | ✅               | ✅
└─ Create reservation        | ❌           | ✅               | ✅
└─ Validation: date logic    | ❌           | ✅ *9            | ✅ *9
└─ Edit own reservation      | ❌           | ✅ *10           | ✅
└─ Edit others' reservation  | ❌           | ❌ *16           | ✅
└─ Change reserver name      | ❌           | ✅ *11           | ✅
└─ Edit resource from res.   | ❌           | ❌               | ✅
└─ Edit res. dates           | ❌           | ✅ (own only)    | ✅
└─ Date picker missing time  | ❌           | ✅ *17           | ✅
/resources                   | ✅ *12       | ✅               | ✅
└─ Add new resource          | ✅ *12       | ❌               | ✅
└─ Symbols & numbers allowed | ✅           | ✅               | ✅
Other :Email uniqueness      | ✅ *13       | ✅ *13           | ✅ *13

---


### Notes:
- *1: Guest can bypass and add resource via direct URL (`/resources`)
- *2: Reserver cannot add new resource
- *3: Admin can add and edit resources
- *4: Cannot register using email that’s already in use
- *5: Email must follow correct pattern (e.g., `@`, no double `@@`)
- *6: Password must be at least 8 characters
- *7: Wrong email or password leads to failed login
- *8: Guest is unauthorized to access `/reservation`
- *9: Start date must be before end date
- *10: Reserver can edit **only** their own reservations
- *11: Reserver can change the reserver name (potential vulnerability)
- *12: Guest can access `/resources` and add resource via routing (security issue)
- *13: Email addresses must be unique
- *14: Minimum age 15 to make a reservation
- *15: Guest can only see reservation data (ambiguous – read-only?)
- *16: Reserver can access and edit others’ reservation via URL (security flaw)
- *17: Time not available in date picker while reserving

### 🔒 ZAP Security Testing – Discovered Endpoints

Below is a list of backend endpoints discovered through OWASP ZAP and verified for accessibility by different user roles.
#### 📋 Endpoint Access Matrix

| **Endpoint URL**                  | **Guest** | **Reserver** | **Admin** | **Notes**                                 |
|----------------------------------|-----------|--------------|-----------|-------------------------------------------|
| `/api/users`                     | ❌        | ❌           | ✅        | Admin-only user list                      |
| `/api/resources`                 | ❌        | ✅           | ✅        | Accessible via `GET`                      |
| `/api/resources/13`              | ❌        | ✅           | ✅        | Resource detail view                      |
| `/api/reservations/14`           | ❌        | ✅           | ✅        | Reserver may access own reservation only? |
| `/api/session`                   | ✅        | ✅           | ✅        | Returns session/login info                |
| `/logout`                        | ❌        | ❌           | ✅        | Admin can log out                         |
| `/register`                      | ✅        | ✅           | ✅        | Registration page                         |
| `/reservation`                   | ❌        | ✅           | ✅        | Reserver can make/edit reservations       |
| `/reservation?id=14`             | ❌        | ✅           | ✅        | Reservation with specific ID              |
| `/resources`                     | ✅        | ✅           | ✅        | Accessible resource list                  |
| `/resources?id=13`               | ✅        | ✅           | ✅        | Resource with specific ID                 |
| `/static/reservationsForm.js`    | ✅        | ✅           | ✅        | Public JS file                            |
| `/static/resourceForm.js`        | ✅        | ✅           | ✅        | Public JS file                            |

---

### Notes:
- **Endpoints like `/api/resources` and `/api/reservations/14`** are accessible by both the reserver and admin, while guests are restricted.
- **Admin-only resources** include `/api/users` and `/logout`.
- **Guest users** have access to public pages such as `/register` and `/static/reservationsForm.js`.
- **Reserver-only** access for endpoints like `/reservation` and `/reservation?id=14` for managing their own reservations.


#### 🧠 Key Observations

- **Guest Access**:
  - Can access static files and session endpoint.
  - Restricted from reservation/resource data.
  - ⚠️ Can try accessing `/resources` via direct URL (`*12`).

- **Reserver Access**:
  - Can access their own resources and reservations.
  - ⚠️ May access or edit others' reservations via ID in URL (`*16`).
  - Can change reserver name (`*11`) — potential impersonation or data integrity risk.

- **Admin Access**:
  - Full access to all endpoints as expected.

