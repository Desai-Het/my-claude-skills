# 🧠 my-claude-skills

A collection of custom Claude skills — each one built to extend what Claude can do in a specific, focused way.

Every skill lives in its own folder and can be installed directly into Claude via the Skills settings on [claude.ai](https://claude.ai).

---

## 📦 Available Skills

| Skill | Description | Trigger |
|-------|-------------|---------|
| [code-breakdown](./code-breakdown/) | Explains any code depth, block by block, adapted to your level | `/code-breakdown` |

> More skills coming as I build them.

---

## 🚀 How to Install a Skill

1. Go to the skill's folder and download the `.skill` file
2. Open [claude.ai](https://claude.ai)
3. Go to **Settings → Skills**
4. Click **Upload Skill** and select the `.skill` file
5. The skill is now active in your Claude

---

## 📁 Repo Structure

```
my-claude-skills/
└── code-breakdown/
    ├── SKILL.md              # Skill logic (readable)
    ├── code-breakdown.skill  # Installable skill file
    ├── README.md             # Skill-specific documentation
    └── LICENSE               # MIT License
```

---

## 📄 License

All skills in this repo are licensed under the [MIT License](./code-breakdown/LICENSE) — free to use, modify, and share. Just keep the credit. 🙌

---

Made by [Het Desai](https://www.linkedin.com/in/hetdesai03/) • [Portfolio](https://het-desai-s1gn0jf.gamma.site/)
