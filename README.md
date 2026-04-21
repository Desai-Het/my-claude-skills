# 🔍 code-breakdown — A Claude Skill for Understanding Code

A structured, personalized Claude skill that explains any code — simple or complex — in a way that actually makes sense to *you*.

Whether you're a complete beginner trying to understand your first Python script, a student debugging an assignment, or an experienced developer doing a quick walkthrough — this skill adapts to your level and walks you through the code step by step.

---

## ✨ What It Does

Most code explanations either go too fast or feel too shallow. This skill fixes that.

When you trigger it, Claude will:

- **Ask you a few quick questions** — your experience level, your goal, and how you'd like to be guided
- **Summarize the code** in plain English before diving in
- **Explain block by block** from top to bottom — what each section does, what it takes in, what it produces
- **Trace the execution flow** from bottom up — what actually runs first, what gets called next, what data moves where
- **Generate visual diagrams** — flowcharts or interactive components to make the flow click visually
- **Test your understanding** at the end with a mini quiz and a "What if?" code challenge

The depth of explanation automatically adjusts based on your level — beginners get every line explained with syntax breakdowns and design reasoning, intermediates get a fast but thorough walkthrough, and experts get a dense summary focused on logic and flow.

---

## 📦 Installation

1. Download the `code-breakdown.skill` file from this repository
2. Open [Claude.ai](https://claude.ai)
3. Go to **Settings → Skills**
4. Click **Upload Skill** and select the downloaded `.skill` file
5. That's it — the skill is now active in your Claude

---

## 🚀 How to Use

Once installed, just type the command below in any Claude conversation:

```
/code-breakdown
```

Then paste your code (or paste the code first, then type the command). Claude will take it from there — starting with a few quick questions before the explanation begins.

**You don't need to describe the code or explain what language it's in.** Claude detects everything automatically.

---

## 💡 Examples

**Example 1 — Beginner asking about a Python function:**
```
/code-breakdown

def calculate_discount(price, percent):
    discount = price * (percent / 100)
    return price - discount
```
→ Claude asks your level → explains every line with syntax → shows a flow diagram → quizzes you at the end

---

**Example 2 — Intermediate user with a Flask API route:**
```
/code-breakdown

@app.route('/users/<int:id>', methods=['GET'])
def get_user(id):
    user = db.session.query(User).filter_by(id=id).first()
    if not user:
        return jsonify({'error': 'Not found'}), 404
    return jsonify(user.to_dict())
```
→ Claude skips the basics → walks through the query, the conditional, and the response → generates an execution flow component

---

**Example 3 — Student with a confusing recursive function:**
```
/code-breakdown

def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)
```
→ Claude traces the recursive calls with a concrete input → generates a call tree diagram → ends with a "What if?" challenge

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) — free to use, share, and modify. Just keep the credit. 🙌

---

Made by [Het Desai](https://www.linkedin.com/in/hetdesai03/) • [Portfolio](https://het-desai-s1gn0jf.gamma.site/)
