# 📚 Prompt Library — ComfyUI Custom Node

A fully-featured prompt manager integrated directly into ComfyUI.
Organize, search, and reuse your AI generation prompts with categories, sub-categories, tags, and negative prompts.

![Preview of Foundation-1 nodes in ComfyUI](assets/prompt-library-preview.png)

---

## ✨ Features

| Feature | Details |
|---|---|
| 📁 **Categories** | Unlimited nesting (categories → sub-categories → …) |
| 🎨 **Color coding** | Each category gets its own color |
| 🔍 **Search** | Full-text search across titles, prompt text, and tags |
| 🏷️ **Tags** | Comma-separated tags on every prompt |
| ➖ **Negative prompts** | Store positive + negative together |
| ↗ **One-click use** | Instantly loads the selected prompt into the node |
| ✎ **Edit in place** | Modal editors for prompts and categories |
| 💾 **Auto-persist** | All data saved to `prompt_library_data.json` |

---

## 🚀 Installation

1. Copy the **entire `prompt_library_node/` folder** into your ComfyUI custom nodes directory:

```
ComfyUI/
└── custom_nodes/
    └── prompt_library_node/   ← paste here
        ├── __init__.py
        ├── prompt_library.py
        ├── prompt_library_data.json   (created automatically on first save)
        └── web/
            ├── prompt_library.js
            ├── prompt_library_style_loader.js
            └── prompt_library.css
```

2. Restart ComfyUI.

3. Find the node under **Add Node → utils/prompts → 📚 Prompt Library**.

---

## 🔌 Node outputs

| Output | Description |
|---|---|
| `positive` | The saved positive prompt text (+ optional prefix/suffix) |
| `negative` | The saved negative prompt text |

### Inputs
| Input | Description |
|---|---|
| `prompt_id` | Auto-filled when you click ↗ on a card |
| `prefix` *(optional)* | Text prepended to the positive prompt |
| `suffix` *(optional)* | Text appended to the positive prompt |

---

## 📂 Data file

All prompts are stored in `prompt_library_data.json` in the node folder.
You can back it up or share it between machines.

---

## 🛠 API endpoints (internal)

| Method | Path | Description |
|---|---|---|
| GET | `/prompt_library/data` | Load full library |
| POST | `/prompt_library/data` | Replace full library |
| POST | `/prompt_library/category` | Create category |
| PUT | `/prompt_library/category/:id` | Update category |
| DELETE | `/prompt_library/category/:id` | Delete category + children |
| POST | `/prompt_library/prompt` | Create prompt |
| PUT | `/prompt_library/prompt/:id` | Update prompt |
| DELETE | `/prompt_library/prompt/:id` | Delete prompt |
