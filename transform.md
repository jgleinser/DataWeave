%dw 2.0
output application/xml
---
{
  root: {
    departments: {
      (payload.root.people.*person map {
        ($.department): {
          employees: {
            employee: {
              fname: $.firstName,
              lname: $.lastName,
              displayName: $.firstName ++ ' ' ++ $.lastName
            }
          }
        }
      })
    }
  }
}