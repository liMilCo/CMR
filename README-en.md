**English** | [فارسی](README.md)

# CMR Printer

A single-file web app for printing text onto **pre-printed CMR consignment notes**.

<img width="1335" height="637" alt="image" src="https://github.com/user-attachments/assets/058e3cca-854e-4c70-9b06-9162e9987e8d" />


Transport companies often work with CMR forms that are already printed with the carrier's logo and layout, and every company's form is slightly different. CMR Printer lets you type the shipment data once, then print only the text so that it lands in the right boxes of the paper form. Each company gets its own alignment (top margin, left margin, font size and the position of every box), and everything is saved in your browser for next time.

- One HTML file. No server, no build step, no dependencies, no internet needed.
- Works offline in any modern browser (Chrome or Edge recommended).
- Supports Latin, Cyrillic and Persian/Arabic text (right-to-left text is detected automatically).
- Your data stays on your computer. Nothing is sent anywhere.

## Features

- **Multiple companies / forms** – separate layout settings for each company's CMR form.
- **Per-company alignment** – top and left offset, font size, line gap, and the exact position and width of every box.
- **Per-box top position** – every box has its own "Top (mm)" field.
- **Drag and drop positioning** – move the boxes directly on the A4 preview.
- **Guide photo** – add a photo of the blank CMR behind the preview to help you align (screen only, never printed).
- **Shared shipment data** – the typed data stays the same when you switch company; only the layout changes.
- **Automatic date** – type `{date}` in a box and it is replaced with today's date at print time.
- **Saved shipments** – save named shipments and load them again later.
- **Backup / restore** – export everything to a file and import it on another computer.
- **Default data from the server** – optional `config.json` placed next to the HTML file is loaded automatically on first use.
- **Print-ready** – prints on A4 with no margins, text only, no background.

## Quick start

1. Download `index.html` (or `cmr-printer.html`).
2. Open it in Chrome or Edge.
3. Fill in the shipment data on the left.
4. Put the pre-printed CMR in the printer, press **Print on CMR**.
5. If the text is not in the right place, adjust the alignment (see below) and print again on a plain sheet of paper first.

> Tip: always do the first test print on plain paper, then hold it against the real CMR in front of a light to check the alignment.

## User guide

### Screen layout

The left panel contains the settings and the form. The right side shows a live A4 preview of exactly what will be printed.

### 1. Companies (CMR forms)

The **Company / CMR form** dropdown selects which company's layout is used.

| Button | What it does |
|---|---|
| **New** | Creates a new company. It starts as a copy of the current company's layout. |
| **Rename** | Renames the current company. |
| **Delete** | Deletes the current company and its layout (at least one company must remain). |

Switching company changes only the layout (margins, font, box positions, guide photo). The typed shipment data is shared and does not change.

### 2. Alignment for this company's form

These settings belong to the selected company.

| Setting | Meaning |
|---|---|
| **Top (mm)** | Moves everything down (positive) or up (negative). Use this first when the whole print is too high or too low. |
| **Left (mm)** | Moves everything right (positive) or left (negative). |
| **Font (pt)** | Text size. Default is 10 pt. |
| **Line gap** | Line spacing multiplier. Default is 1.15. |

Buttons:

- **Move fields on preview** – turns on layout mode (see below).
- **Add form photo** – shows a photo of the blank CMR behind the preview.
- **Remove photo** – removes the guide photo.
- **Reset to default** – resets margins, font and all box positions of this company to the defaults. Your typed data and photo are kept.

#### Moving boxes

1. Press **Move fields on preview**. The boxes get a blue dashed outline and a label.
2. Drag a box to the right place. Positions snap to 0.5 mm.
3. Click a box to select it. You can then type exact **X**, **Y** and **Width** values (in mm), or press **Reset** to return that box to its default position.
4. Press **Done moving fields** when finished.

Every box also has a **Top (mm)** field next to its name in the form. It is the distance of that box from the top of the page, so you can adjust a single box without dragging.

#### Guide photo

Press **Add form photo** and choose a photo or scan of the blank CMR. It is shown faintly behind the preview to help you place the boxes. Notes:

- It is stretched to fit A4, so treat it only as a rough guide.
- It is only shown on screen. It is never printed.
- It is saved with the company.

### 3. Shipment data

Fill in the boxes. The numbers match the CMR form.

| Box | CMR field |
|---|---|
| 1 Sender | Sender (name, address, country) |
| 2 Consignee | Consignee (name, address, country) |
| 3 Place of delivery | Place of delivery of the goods |
| 4 Place & date of taking over | Place and date of taking over the goods |
| 5 Documents attached | Documents attached |
| 6-9 Marks, packages, packing, goods | One big box for marks and numbers, number and method of packing, and nature of the goods (text is centered) |
| 10 Statistical number | Statistical number |
| 11 Gross weight (kg) | Gross weight (printed in bold) |
| 12 Volume (m3) | Volume |
| 13 Sender's instruction | Sender's instructions |
| 18 Carrier reservations | Carrier's reservations and observations (driver, truck, pass number, etc.) |
| 21 Established in | Place where the CMR is established |
| 21 Date | Date of the CMR |

Each box can have several lines. Press Enter for a new line. Persian and Arabic text is printed right-to-left automatically.

**Clear form** empties all shipment data.

#### Automatic date

Type `{date}` in any box and it is replaced with the date when printing. This is used by default in boxes 4 and 21 Date.

Above the form you can change:

- **Print date** – defaults to today. Pick another day to print a CMR for a different date.
- **Date format** – `YYYY/MM/DD` (default), `YYYY-MM-DD`, `DD.MM.YYYY` or `DD/MM/YYYY`.
- **Today** – resets the print date to today.

The print date is not saved, so every time you open the app it starts on today.

### 4. Saved shipments

Use this to keep frequently used shipments.

1. Fill in the form.
2. Type a name (for example "Arcolev - 19 Oct") and press **Save**.
3. Later press **Load** next to the name to fill the form again, or the cross to delete it.

### 5. Printing

Press **Print on CMR**. In the browser's print dialog set:

- Paper size: **A4**
- Margins: **None**
- Scale: **100%** (not "Fit to page")
- Headers and footers: **Off**

Only the text is printed. The page background, the guide photo and the layout outlines are never printed.

### 6. Backup, restore and sharing settings

Everything (companies, layouts, guide photos, shipment data, saved shipments and date format) is stored in your browser. Browsers can clear this data, and it is not shared between different browsers or computers, so export a backup now and then.

| Button | What it does |
|---|---|
| **Export Data** | Saves everything to a `.json` file. |
| **Import Data** | Loads a previously exported file and replaces the current data. |
| **Load from server** | Loads `config.json` from the server and replaces the data in this browser (it asks first). |

#### Using the same setup on several computers

1. On the computer with the correct setup, press **Export Data**.
2. Rename the downloaded file to **`config.json`**.
3. Upload it to the web server in the same folder as the HTML file.
4. On other computers, open the page. A browser that has no saved data loads `config.json` automatically on first use. A browser that already has data keeps it; press **Load from server** there to take the newer setup.

If `config.json` does not exist, the app simply starts with built-in sample data. Loading `config.json` only works when the page is opened from a web server (`http://` or `https://`); when you open the HTML file directly from your disk, use **Import Data** instead.

> **Privacy warning:** `config.json` contains your companies and shipment data. Do not publish a real `config.json` in a public GitHub repository or on a public web page. Only put it on a private server.

## Hosting on GitHub Pages (optional)

You can host the app so you can open it from anywhere:

1. Rename `cmr-printer.html` to `index.html` and commit it to the repository.
2. In the repository go to **Settings > Pages**, choose the branch (for example `main`) and the root folder, and save.
3. Open the address GitHub shows, usually `https://<username>.github.io/<repository>/`.

Data saved in the browser belongs to the page address, so the GitHub Pages copy and a copy opened from your disk have separate data. Use Export and Import to move between them.

## How data is stored

- Saved in the browser's `localStorage` under the key `cmrPrinter.v1`.
- The data is stored per browser, per browser profile and per page address.
- Private/incognito windows do not keep the data.
- Guide photos are shrunk (about 900 px wide) before saving to save space.

### `config.json` format

`config.json` is the same file the **Export Data** button creates. It is plain JSON:

```json
{
  "current": "abc123",
  "profiles": {
    "abc123": {
      "name": "Company 1",
      "offTop": 0,
      "offLeft": 0,
      "font": 10,
      "lh": 1.15,
      "pos": {},
      "bg": ""
    }
  },
  "data": { "sender": "...", "consignee": "..." },
  "records": [],
  "dateFmt": "YYYY/MM/DD",
  "dateTok": true
}
```

- `profiles` – one entry per company; `pos` holds the custom x, y and width (mm) of the boxes that were moved.
- `data` – the shipment data shared by all companies.
- `records` – the saved shipments.

## Troubleshooting

**The text prints in the wrong place.** Check the print dialog: margins must be "None" and scale "100%". Then adjust the company's **Top (mm)** and **Left (mm)**, or move individual boxes.

**Everything is shifted by a small constant amount.** Some printers have a built-in unprintable margin. Compensate with the company's Top and Left values.

**A long text does not fit its box.** Make the box wider (select it in layout mode and change **Width**), reduce the font size, or split the text over more lines.

**My data disappeared.** The browser data was probably cleared, or you opened the app from a different address or browser. Restore it with **Import Data** (or **Load from server**).

**"Load from server" says config.json was not found.** The file must be named exactly `config.json`, be valid JSON, and be in the same folder as the page. It does not work when the HTML file is opened directly from disk.

**The dropdown text is hard to read.** Use an up-to-date Chrome, Edge or Firefox.

## Project structure

```
.
├── index.html    # the whole application (HTML, CSS and JavaScript)
├── config.json   # optional default data (do not publish real data)
├── README.md     # English documentation
└── README-fa.md  # Farsi documentation
```

## Customizing

All box positions are defined in the `FIELDS` list near the top of the script in the HTML file. Each entry has a key, a label, the default `x`, `y` and `w` (width) in millimetres on an A4 page, the number of rows in the form, and optional `align` and `bold` settings. The sample data is in the `SAMPLE` object right below it.

## Contact
🙋‍♀️ If you have any questions or concerns, please feel free to reach out to us via our discussions tracker.

## Donations
* USDT-TRC20 or TRX:
```
TEA6H5EgqVsUXF1A157pFhVgpgtcLp2BMa
```
