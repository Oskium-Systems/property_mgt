## 🗂️ Layout Architecture

This project uses **three separate Blade layouts**, each serving a specific purpose.
All modules extend the appropriate layout based on context.

---

### `resources/views/layouts/app.blade.php`
Used by **authentication pages** (Login, Register, Forgot Password, etc.)

> Powered by Laravel Breeze. These views live in `resources/views/auth/`.
```blade
@extends('layouts.app')
```

---

### `resources/views/layouts/admin.blade.php`
Used by modules accessible to **admin users** after login.
```blade
@extends('layouts.admin')
```

---

### `resources/views/layouts/user.blade.php`
Used by modules accessible to **regular authenticated users** after login.
```blade
@extends('layouts.user')
```

---

### Summary Table

| Layout | Used For | Who Sees It |
|---|---|---|
| `layouts.app` | Login, Register, Password Reset | Guest / Unauthenticated |
| `layouts.admin` | Admin dashboard & admin modules | Authenticated Admins |
| `layouts.user` | User dashboard & user modules | Authenticated Users |

---

### ⚠️ Important Notes

- **Authentication is handled entirely by Laravel Breeze** — do not create a separate Auth module.
- The root URL `/` redirects to `/login` automatically.
- All new modules must extend **one** of the three layouts above depending on who accesses it.
- Layouts live in `resources/views/layouts/` and are **shared globally** across all modules.
