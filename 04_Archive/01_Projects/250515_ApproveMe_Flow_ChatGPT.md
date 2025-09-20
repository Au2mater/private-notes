Perfect — let’s wireframe both the **revised linear flow** _with the new “Reviewer Access” step_, and the **home screen/dashboard** for returning users.

---

## **1. Linear Flow Wireframe (for First-Time Users)**

### **Progress Bar:**

```
[1. Import Data] → [2. Design Layout] → [3. Reviewer Access] → [4. Preview & Publish]
```

---

### **Step 1: Import Data**

```
--------------------------------------
| Import your dataset                |
| [ Drop file here or Browse ]       |
|                                    |
| Supported: CSV, XLSX               |
--------------------------------------
| ➔ Next: Design Layout              |
```

---

### **Step 2: Design Layout**

```
--------------------------------------
| Choose how your data is presented |
| [Column list with drag & drop]    |
| [Show/Hide] [Rename] [Pin]        |
--------------------------------------
| ➔ Next: Reviewer Access           |
```

---

### **Step 3: Reviewer Access** _(New Step)_

```
--------------------------------------
| Control who sees what             |
|                                  |
| [Dropdown: Select column to use  |
|  for reviewer filtering — e.g.   |
|  user_email / region / team]     |
|                                  |
| Reviewer Mapping Table:          |
|  Reviewer Email   |  Value(s)    |
|  alice@...        |  Region A    |
|  bob@...          |  Region B    |
|  [+ Add Reviewer]                |
--------------------------------------
| ? What's this? (tooltip/help)     |
| ➔ Next: Preview & Publish         |
```

---

### **Step 4: Preview & Publish**

```
--------------------------------------
| This is what reviewers will see   |
| [ Table Preview ]                 |
|                                  |
| [ Publish ] [ Save as Draft ]    |
|                                  |
| Need changes? [← Go Back]        |
--------------------------------------
```

---

## **2. Returning User Home Screen Wireframe**

### **Home / Dashboard View**

```
--------------------------------------
| Welcome back to ApproveMe         |
|                                  |
| [ Continue where I left off ]    |
| [ Start a New Dataset ]          |
|                                  |
| ───── My Datasets ─────          |
| Name         | Status  | Actions |
| Sales_Q1     | Draft   | [Edit]  |
| Audit_Logs   | Live    | [Preview] [Unpublish] [Edit] |
--------------------------------------
```

---

### **Status Tooltips & Tags**

- **Draft:** In progress, not yet shared.
- **Live:** Published, visible to reviewers.
- **Archived:** Old versions or retired sets.

---

I can convert this into a clickable Figma-style layout, or help you start applying this step-by-step in your current HTML structure. Would you like a visual mockup next or code scaffold of the new step?