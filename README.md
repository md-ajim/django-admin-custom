# 🛠️ Unfold Admin Panel Customization

A modern, professional, and fully customizable Django Admin panel interface powered by [django-unfold](https://github.com/unfoldadmin/unfold). This configuration improves admin UX/UI with branding, theming, and user management enhancements.

---

## 📁 Project Structure Overview

```
project_root/
├── your_app/
├── static/
│   ├── css/style.css
│   ├── js/script.js
│   ├── icons/
│   │   ├── icon-light.svg
│   │   └── icon-dark.svg
│   ├── logos/
│   │   ├── logo-light.PNG
│   │   └── logo-dark.svg
│   └── favicons/favicon.svg
├── templates/
├── unfold_callbacks.py
├── settings.py
└── README.md
```

---

## 🚀 Features

✅ Fully branded admin interface
✅ Sidebar navigation with grouping & permissions
✅ Themed login background and layout
✅ Custom icons, logos, and favicons
✅ Tabbed model view support
✅ Support for multi-language flags
✅ Ready-to-use user management dashboard

---

## 🔧 Configuration Details

### UNFOLD Settings (in `settings.py` or custom config module)

```python
UNFOLD = {
    "SITE_TITLE": "Customize Admin Panel",
    "SITE_HEADER": "Admin Panel",
    "SITE_SUBHEADER": "Manage Users and Access",
    "SITE_URL": "/",
    "SITE_ICON": {
        "light": lambda request: static("icons/icon-light.svg"),
        "dark": lambda request: static("icons/icon-dark.svg"),
    },
    "SITE_LOGO": {
        "light": lambda request: static("logos/logo-light.PNG"),
        "dark": lambda request: static("logos/logo-dark.svg"),
    },
    "SITE_FAVICONS": [
        {
            "rel": "icon",
            "sizes": "32x32",
            "type": "image/svg+xml",
            "href": lambda request: static("favicons/favicon.svg"),
        },
    ],
    "SITE_DROPDOWN": [
        {
            "icon": "diamond",
            "title": _("Portfolio"),
            "link": "https://ajim-dev.vercel.app/",
        },
    ],
    "SITE_SYMBOL": "speed",
    "SHOW_HISTORY": True,
    "SHOW_VIEW_ON_SITE": True,
    "SHOW_BACK_BUTTON": True,
    "ENVIRONMENT": environment_callback,
    "ENVIRONMENT_TITLE_PREFIX": environment_title_prefix_callback,
    "DASHBOARD_CALLBACK": dashboard_callback,
    "THEME": True,
    "LOGIN": {
        "image": lambda request: static("images/login-bg.jpg"),
        "redirect_after": lambda request: reverse_lazy("admin:auth_user_changelist"),
    },
    "STYLES": [
        lambda request: static("css/style.css"),
    ],
    "SCRIPTS": [
        lambda request: static("js/script.js"),
    ],
    "BORDER_RADIUS": "8px",
    "COLORS": {
        "base": {
            "50": "249 250 251",
            "100": "243 244 246",
            ...
        },
        "primary": {
            "50": "240 249 255",
            ...
        },
        "font": {
            "subtle-light": "var(--color-base-500)",
            ...
        },
    },
    "EXTENSIONS": {
        "modeltranslation": {
            "flags": {
                "en": "🇬🇧",
                "bn": "🇧🇩",
            },
        },
    },
    "SIDEBAR": {
        "show_search": True,
        "show_all_applications": True,
        "navigation": [
            {
                "title": _("User Management"),
                "separator": True,
                "collapsible": True,
                "items": [
                    {
                        "title": _("Dashboard"),
                        "icon": "dashboard",
                        "link": reverse_lazy("admin:index"),
                        "permission": lambda request: request.user.is_superuser,
                    },
                    {
                        "title": _("Users"),
                        "icon": "people",
                        "link": reverse_lazy("admin:auth_user_changelist"),
                        "permission": lambda request: request.user.is_staff,
                    },
                ],
            },
        ],
    },
    "TABS": [
        {
            "models": [
                "auth.user",
            ],
            "items": [
                {
                    "title": _("All Users"),
                    "link": reverse_lazy("admin:auth_user_changelist"),
                    "permission": lambda request: request.user.is_staff,
                },
            ],
        },
    ],
}
```

---

## 📸 Screenshots

Include clean screenshots of:

* Login screen
* Admin dashboard
* User list with tab views

---

---

## ✅ Requirements

* Python 3.8+
* Django 4.2+
* `django-unfold` (UI customization plugin)

---

## ⚙️ Setup Instructions

```bash
pip install django-unfold
```

Add `'unfold'` to `INSTALLED_APPS` **before** `'django.contrib.admin'`:

```python
INSTALLED_APPS = [
    'unfold',
    'django.contrib.admin',
    ...
]
```

Then load the config (`UNFOLD`) in your settings.

---

## 📎 Useful Links

* 🔗 [Unfold Documentation](https://github.com/unfoldadmin/unfold)
* 🔗 [Live Portfolio](https://ajim-dev.vercel.app/)

---

## 🙌 Author

**Ajim Uddin**
💼 Full-stack Developer
🌐 [Portfolio](https://ajim-dev.vercel.app/)
📧 [ajim@example.com](mailto:ajim@example.com)

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).


