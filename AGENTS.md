# AGENTS: NexPort Developer Guide

Scope

- This file governs the entire repository. Follow these instructions for any file you add or modify.

Purpose

- This repo contains developer documentation for NexPort Products.
- Documentation is authored in Markdown and organized for GitBook.

Location (Important)

- All GitBook content lives under the root of the repository.
- The GitBook entry files are `README.md` and `SUMMARY.md`.
- Images and other assets should be stored under `assets/`.
- Gitbook stores images under .gitbook/assets and that's fine

Authoring Rules (GitBook‑Friendly)

- Markdown only. Avoid raw HTML and complex embeds. Except where gitbook uses it like <figure>
- Use relative links between pages (e.g., `../admin/products.md`).
- Keep headings concise and semantic.
- Heading hierarchy: one H1 (`#`) per page for the title. Use H2 (`##`) for top‑level sections, H3 (`###`) for subsections, and H4 (`####`) only when truly necessary.
- Do not skip heading levels (e.g., don’t jump from H2 to H4). Avoid using bold text as a “fake” heading.
- Align the page H1 with the intent of the item in `SUMMARY.md` (the SUMMARY label can be longer; the H1 should stay concise).
- Bullets should be short, one line where possible.
- Use blockquotes for callouts: `> Note`, `> Tip`, `> Warning`.
- Keep pages focused; split very long topics when a natural break exists.
- No secrets, tokens, or internal bug‑tracker links in public docs.
  - Internal links: always use Markdown link syntax with relative paths (e.g., `[Orders & Fulfillment](orders.md)` or `[Assigning and Transferring NexPort Campus Seats](assigning-and-transferring-seats/README.md)` when linking to a grouped page).

Legacy Documents

- Some patterns and documentation ARE OUT OF DATE. Always try to identify what docs need to be marked out of date.



Project Structure

- `Needs to be refined

Style & Terminology

- Product names: NexPort Marketplace, NexPort Campus, NexPort Analytics.
- Prefer conceptual phrasing like “Organization purchases”, “seats”, and “Assigning and Transferring NexPort Campus Seats” in page titles. Reserve “wholesale” for explicit UI/setting labels (e.g., sale model = wholesale).
- Use Title Case for section headers; sentence case for body text.
- Prefer active voice and present tense.
- Keep link text meaningful (avoid “click here”).
- When listing UI, match observed labels (e.g., `Administrator`, `Create/Edit Mapping`, `Redeem`).

Headings with Subpages

- It’s valid (and common) for GitBook to turn a page into a folder with a `README.md` and subpages (e.g., `admin-guide/assigning-and-transferring-seats/README.md`).
- When this happens, update any internal links to point to the folder path or its `README.md` explicitly (e.g., `assigning-and-transferring-seats/README.md`).
- Subpages live under the same folder. Add them to `SUMMARY.md` beneath the parent heading if you want them surfaced in the sidebar.
  - SUMMARY example:
    - `[Assigning and Transferring NexPort Campus Seats](admin-guide/assigning-and-transferring-seats/README.md)`
    - `  * [Sub Page Test](admin-guide/assigning-and-transferring-seats/sub-page-test.md)`

Content Sources (internal)



Operational Notes

- Provide clear examples of usage.



Contribution Workflow

- One topic per PR; keep diffs small and focused.
- Validate Markdown renders correctly in GitBook (headings, lists, links, images).
- If adding images, compress and keep widths reasonable (≤1200px preferred) and store under `/assets/`.
- Update `/SUMMARY.md` alongside any new page.

Known Page Map (baseline under `/`)

- Overview: `README.md`
  
  

Contact

- If requirements change (new flows, labels), update both the relevant page(s) and this AGENTS file when guidance needs to change.

GitBook Variables

- Use variables defined in `.gitbook/vars.yaml` via inline expressions: `<code class="expression">space.vars.PRODUCT_NAME</code>`.
- Prefer variables for frequently repeated names (e.g., product name) rather than hard‑coding strings across pages.
- If you add a new variable in GitBook, reference it as `space.vars.YOUR_KEY` in Markdown. Coordinate default values with the docs team.
- Do not commit secrets into variables; GitBook variables are for display content only.
  

Available variables (current)

- 

Mermaid Diagrams

- Use fenced code blocks with the `mermaid` language fence:
  
  ```
  ```mermaid
  flowchart LR
    A["Available"]
    B["Awaiting (emailed)"]
    C["Assigned / Redeemed"]
    A -- Assign --> C
    A -- Email redemption --> B
  ```
  
  ```
- Quote node labels that include parentheses, slashes, or special punctuation to ensure GitBook’s Mermaid renderer parses them (e.g., `B["Awaiting (emailed)"]`).
- Keep separate diagrams where admin and store (purchasing agent) flows differ; label sections clearly (e.g., "Status flow (Admin)" and "Status flow (Store)").
- Validate diagrams in GitBook after sync; if rendering fails, check for quoting on node labels and consistent code fences.
