# SKILL.md — Food Diary / Calendar Sticker Production

## Purpose

This repository is used to batch-produce food scrapbook/sticker edits for **Diary** and **Calendar** screenshots.

The goal is NOT to redesign the app UI.

The goal is to preserve the supplied screenshot as a **LOCKED BASE IMAGE** and add food stickers that look like they were cut out from ordinary phone snapshots and pasted into a casual food journal.

---

# 1. Highest-priority rule: preserve the original screenshot

Treat every input screenshot as a **LOCKED BASE IMAGE**.

Unless the task explicitly says otherwise:

- Keep the original canvas dimensions exactly.
- Keep the original aspect ratio exactly.
- Do NOT crop the screenshot.
- Do NOT stretch or squash the screenshot.
- Do NOT redraw, recreate, beautify, or reinterpret the UI.
- Do NOT change existing text, numbers, dates, icons, buttons, navigation, colors, spacing, borders, cards, status bar, or background.
- Do NOT translate existing UI text.
- Do NOT replace existing screenshots with a newly generated approximation.
- Do NOT change the position or size of existing UI elements.
- Only add the requested sticker/journal elements on top of the original screenshot.

The final result should look like:
**original screenshot + manually pasted scrapbook food stickers**.

Not:
**AI recreated the whole app screen**.

---

# 2. Determine task type first

Before editing, classify the input as:

- `DIARY`
- `CALENDAR`

Never mix the two reference systems.

## DIARY

Use the references in:

```text
references/diary/
```

Diary stickers may include:

- larger food cutouts;
- irregular white sticker borders;
- food names;
- kcal labels;
- small hand-drawn arrows;
- tiny hearts, lines, sparkles, or casual doodles;
- relaxed scrapbook composition.

The result should feel like a personal food diary made by a normal user.

## CALENDAR

Use the references in:

```text
references/calendar/
```

Calendar stickers must be:

- much smaller;
- compact;
- readable at calendar-cell size;
- positioned inside the corresponding date cell;
- visually subordinate to the existing calendar information;
- consistent across the month without looking mechanically duplicated.

Do NOT turn calendar cells into large poster-style illustrations.

---

# 3. Reference hierarchy

References are mandatory visual guidance.

When available, prioritize them in this order:

1. task-specific finished sticker references;
2. task-specific food-realism references;
3. the current input screenshot;
4. this written style guide.

For a Diary task, use only Diary references for layout/style.

For a Calendar task, use only Calendar references for layout/style.

Do not copy the exact food from a reference unless explicitly requested. References define the **visual language**, not necessarily the food content.

---

# 4. Food realism — CRITICAL

This is one of the most important requirements.

Food should look like it came from an ordinary person's phone photo.

Target feeling:

> casual iPhone snapshot → subject cut out → white sticker border added

Food must NOT look like:

- commercial food photography;
- studio photography;
- restaurant advertising;
- stock photography;
- glossy product photography;
- hyperrealistic AI food;
- perfectly styled editorial food;
- 3D render;
- illustration;
- plastic-looking food.

Prefer:

- ordinary indoor lighting;
- slightly imperfect exposure;
- natural shadows;
- minor phone-camera softness;
- realistic texture;
- imperfect food arrangement;
- normal bowls, plates, takeaway boxes, cups, wrappers, trays;
- slightly inconsistent angles;
- everyday portions;
- believable leftovers or casual plating when appropriate.

Avoid:

- dramatic rim lighting;
- cinematic lighting;
- extreme depth of field;
- perfect symmetry;
- excessive saturation;
- excessive sharpness;
- glossy highlights everywhere;
- flawless restaurant plating;
- floating objects;
- fake-looking steam;
- unrealistically clean food edges.

The image may be attractive, but it must first feel **ordinary and believable**.

When uncertain, choose:
**more mundane / more casual / more phone-photo-like**.

---

# 5. Sticker cutout treatment

Food stickers should generally have:

- irregular subject-aware cutout;
- visible white border;
- softly imperfect contour;
- subtle separation from the background;
- optional very light natural shadow.

The border should follow the actual food/container silhouette.

Do NOT use:

- perfect rectangular photo cards unless the reference calls for them;
- huge uniform white outlines;
- neon outlines;
- hard vector-like edges;
- heavy drop shadows;
- glossy sticker effects.

For objects photographed while being held, the hand may remain part of the sticker if it makes the result feel more authentic.

---

# 6. Diary composition rules

Diary pages should feel casually composed rather than grid-perfect.

Typical composition:

- approximately 3–6 main food stickers depending on available space;
- varied sticker sizes;
- slight rotation where natural;
- asymmetric placement;
- enough whitespace to keep the original diary readable;
- labels close to the corresponding food.

Food can include:

- breakfast;
- lunch;
- dinner;
- snacks;
- drinks;
- fruit;
- takeaway;
- packaged food.

Do not make every item the same size.

Do not cover important existing UI.

Small doodles are optional and should remain secondary.

---

# 7. Diary labels

When labels are requested, use a casual handwritten/scrapbook feeling consistent with the references.

Typical structure:

```text
食物名称
≈ 420 kcal
```

or

```text
早餐
≈ 420 kcal
```

Do not invent calories when accurate values are required and no values are provided.

If calorie values are not supplied and the task is purely visual, omit them unless the user explicitly requests estimated values.

Do not add unnecessary promotional copy.

---

# 8. Calendar composition rules

Calendar edits require much tighter control.

For each recorded date:

- place the food sticker inside the correct date cell;
- keep the date readable whenever possible;
- keep existing calorie/activity labels readable;
- keep stickers small enough to belong to the calendar;
- preserve the original grid;
- preserve the original UI.

Use a variety of ordinary foods rather than repeating the same item excessively.

Examples:

- coffee;
- iced latte;
- sandwich;
- noodles;
- rice bowl;
- salad;
- yogurt bowl;
- toast;
- fruit;
- dumplings;
- takeaway meal;
- bakery item;
- simple home-cooked food.

Sticker scale should feel similar to the approved Calendar references.

Do not fill intentionally empty dates unless instructed.

If the screenshot contains only a certain number of recorded days, preserve that logic.

---

# 9. Variety rules

For batch generation, avoid obvious repetition.

Vary:

- food type;
- container;
- viewing angle;
- scale;
- orientation;
- lighting;
- sticker silhouette.

However, all stickers within one output should still feel like they belong to the same casual visual world.

Do not generate a month where every meal looks like it came from the same studio shoot.

---

# 10. Existing food photos

If food photos are provided in:

```text
input/food_photos/
```

prefer using those photos.

When using supplied photos:

- preserve their recognizable content;
- remove/cut out only the unwanted background;
- keep natural phone-photo texture;
- do not beautify them into commercial food photography;
- add the appropriate white sticker border;
- place them according to the relevant Diary or Calendar reference.

---

# 11. Prohibited changes

Unless explicitly requested, NEVER:

- change screenshot dimensions;
- change screenshot aspect ratio;
- crop the app screenshot;
- redraw the UI;
- replace fonts;
- translate UI;
- change dates;
- change calorie/activity numbers;
- change body weight;
- change mood icons;
- change navigation;
- remove app controls;
- add fake app features;
- add fake logos;
- add unrelated text;
- add watermarks;
- add promotional slogans;
- alter the phone status bar;
- fill every empty date automatically.

---

# 12. Output rules

Save finished files to:

```text
output/diary/
```

or:

```text
output/calendar/
```

according to task type.

Recommended naming:

```text
<original-name>_sticker.png
```

Example:

```text
diary_0929.png
→ output/diary/diary_0929_sticker.png
```

Never overwrite the original input unless explicitly instructed.

---

# 13. Batch workflow

For every input image:

1. Identify whether it is Diary or Calendar.
2. Load the corresponding reference set.
3. Inspect the original dimensions.
4. Lock the screenshot as the base image.
5. Identify safe areas where stickers may be added.
6. Select or create ordinary phone-photo-style food imagery.
7. Cut food into irregular sticker shapes.
8. Add restrained white borders.
9. Compose according to the correct reference family.
10. Preserve all original UI.
11. Export at the exact original pixel dimensions.
12. Compare the output against the input and references before accepting it.

---

# 14. Quality-control checklist

Before saving any result, verify ALL of the following:

- [ ] Canvas dimensions equal the input dimensions.
- [ ] Aspect ratio is unchanged.
- [ ] Original UI has not been redrawn.
- [ ] Existing text is unchanged.
- [ ] Existing numbers are unchanged.
- [ ] Existing icons/buttons are unchanged.
- [ ] Diary/Calendar references were not mixed.
- [ ] Food looks like ordinary phone photography.
- [ ] Food does NOT look like studio/stock/AI food photography.
- [ ] Sticker borders look natural.
- [ ] Stickers do not cover critical UI.
- [ ] Layout resembles the approved references.
- [ ] No unnecessary text or decoration was added.
- [ ] Empty/recorded dates preserve the intended source logic.
- [ ] Output is saved in the correct folder.

If any item fails, revise before exporting.

---

# 15. Visual decision rule

When choosing between:

A. cleaner, prettier, more commercial-looking food

and

B. slightly imperfect, ordinary, believable phone-photo food

always choose **B**.

When choosing between:

A. recreating the screenshot to make composition easier

and

B. preserving the original screenshot exactly and adapting stickers around it

always choose **B**.

The original screenshot is the source of truth.
