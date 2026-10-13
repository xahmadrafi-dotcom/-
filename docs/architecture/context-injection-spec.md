# প্রসঙ্গ-ইনজেকশন বিশেষ নির্দেশিকা

---

## উদ্দেশ্য

এই নির্দেশিকা বর্ণনা করে কীভাবে M99 প্রকল্পের প্রেক্ষাপট তথ্য (context) এআই মডেলে সরবরাহ করতে হয়।
প্রতিটি নতুন কথোপকথনে বা সেশনে যেন সঠিক তথ্য, নিয়ম ও অবস্থা পাঠানো যায়—সেই পদ্ধতি এখানে সাজানো হয়েছে।

---

## প্রযোজ্য ক্ষেত্র

- নতুন চ্যাট সেশন শুরু করার সময়
- একটি এআই মডেল থেকে অন্য এআই মডেলে হ্যান্ডঅফের সময়
- `QUICK_START.md` বা `_HANDOFF_TEMP.md` ব্যবহার করে context পুনরুদ্ধারের সময়
- TONTRA কর্মপ্রবাহের যেকোনো ধাপে যেখানে অবস্থা জানানো প্রয়োজন

---

## ব্যবহার পদ্ধতি

নতুন সেশনে নিচের ধাপ অনুসরণ করতে হবে:

### ধাপ ১ — প্রেক্ষাপট ব্লক পাঠানো

```text
repo: xahmadrafi-dotcom/-
branch: main
নিয়ম: আগে পরিকল্পনা, পরে কাজ। commit-এর আগে confirm।
প্রথম কাজ: MOTHER_TANTRA_INDEX.md দেখো, কী বাকি আছে বলো।
```

### ধাপ ২ — মূল ফাইলের সংযোগ

নিচের ফাইলগুলো প্রেক্ষাপট হিসেবে দিতে হবে:

```text
প্রাথমিক: _HANDOFF_TEMP.md
সূচি: MOTHER_TANTRA_INDEX.md
দ্রুত শুরু: QUICK_START.md
বীজ-মানচিত্র: core/unicode-seed-map.json
```

### ধাপ ৩ — নিয়ম স্তর পাঠানো

```yaml
context_rules:
  language: "Bengali-first"
  code_blocks: "English keys only"
  planning: "before action"
  commit: "confirm before pushing"
  versioning: "ঐ ভার্সনিং"
```

---

## সতর্কতা

- প্রেক্ষাপট ব্লকে কখনো পাসওয়ার্ড বা গোপন তথ্য রাখা যাবে না।
- এআই মডেলকে ঈমান বা মানবতার ওপরে বসানো যাবে না।
- প্রতিটি সেশনে `_HANDOFF_TEMP.md` আপডেট না হলে পরবর্তী সেশনে তথ্য হারিয়ে যেতে পারে।
- encoding ভাঙলে বাংলা টেক্সট ঠিকমতো রেন্ডার না-ও হতে পারে—তাই UTF-8 নিশ্চিত করতে হবে।

---

## উদাহরণ

### সম্পূর্ণ context injection ব্লক:

```yaml
session_context:
  repo: "xahmadrafi-dotcom/-"
  branch: "main"
  active_file: "_HANDOFF_TEMP.md"
  project: "M99"
  version: "ঐ ০.০২"
  current_task: "docs restructure"
  companions:
    - name: "Copilot"
      role: "language, structure, schema"
    - name: "ChatGPT"
      role: "analysis, centers, philosophy"
    - name: "Replit"
      role: "testing, scripting"
    - name: "Vercel"
      role: "publishing, interface"
  rules:
    - "Bengali outside code blocks"
    - "English keys inside code blocks"
    - "plan before action"
    - "confirm before commit"
```

### সংক্ষিপ্ত context injection ব্লক:

```json
{
  "repo": "xahmadrafi-dotcom/-",
  "branch": "main",
  "project": "M99",
  "version": "ঐ ০.০২",
  "handoff": "_HANDOFF_TEMP.md"
}
```

---

## পরিবর্তন-ইতিহাস

| সংস্করণ | তারিখ | পরিবর্তন |
|---------|-------|----------|
| ঐ ০.০১ | ২০২৬-০৬-২৪ | প্রথম সংস্করণ তৈরি |
