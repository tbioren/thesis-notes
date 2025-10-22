## Questions
```dataviewjs
for (let page of dv.pages("#question")) {
  for (let block of page.file.tasks.concat(page.file.lists)) {
    if (block.text.includes("#question")) {
      // keep original block text
      let display = block.text.replace("#question", "");
      let link = dv.fileLink(page.file.path, false, "Link to Note");

      // render block + link at the end
      dv.paragraph(display + " " + link);
    }
  }
}
```
## Work Log

### Fall Quarter

```dataviewjs
// Collect daily notes from "log"
let pages = dv.pages('"log"').where(p => p["Hours Worked"]);
pages = pages.sort(p => p.file.name);

// Extract dates & cumulative actual hours
let dates = [];
let cumulative = [];
let total = 0;

for (let p of pages) {
    dates.push(p.file.name);
    total += p["Hours Worked"];
    cumulative.push(total);
}

// --- Ideal burnup line setup (vanilla JS) ---
function daysBetween(d1, d2) {
    return (d2 - d1) / (1000 * 60 * 60 * 24);
}

let startDate = new Date("2025-09-04");
let endDate   = new Date("2025-11-20");
let totalGoal = 100;
let duration  = daysBetween(startDate, endDate);

// Generate ideal values for each actual date
let ideal = dates.map(d => {
    let current = new Date(d);
    let elapsed = daysBetween(startDate, current);
    if (elapsed < 0) return 0;
    if (elapsed > duration) return totalGoal;
    return (elapsed / duration) * totalGoal;
});

// --- Build chart block for Charts plugin ---
let chart = "```chart\n";
chart += "type: line\n";
chart += "labels: " + JSON.stringify(dates) + "\n";
chart += "series:\n";
chart += "  - title: Cumulative Hours\n";
chart += "    data: " + JSON.stringify(cumulative) + "\n";
chart += "  - title: Ideal Progress\n";
chart += "    data: " + JSON.stringify(ideal) + "\n";
chart += "```";

dv.el("div", chart);
```

#### Week 1 Summary

- I created this Obsidian Notebook and git repo.
- I organized times to meet with Eduardo.
- I began reading my first paper and established expectations for the quarter.

#### Week 2 Summary

- Modified the burnup chart so it's embedded in this work log note instead of in a separate Excel sheet.
- I read the slides and watched the accompanying YouTube video for [[Julian Miller - Tutorial CGP]].
- I decided to focus on designing the experiment for a [[Pico-Ice]] FPGA board because it's similar to EHW and hopefully will be easy to cross-reference bitstream performance in the future.
- It looks like the FPGA is supported by [[Project IceStorm]], so it should be plug and play for EHW.