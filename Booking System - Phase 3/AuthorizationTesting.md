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
