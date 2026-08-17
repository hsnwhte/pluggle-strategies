# Learn Lean Sigma 8D Excel Mapper (v1.0)

Maps an 8D Problem Solving Excel workbook into structured JSON, ready for loading into a
database or passing to another system.

## Source template

Built against the **8D Problem Solving Template** published by Learn Lean Sigma:

<https://www.learnleansigma.com/template/8d-problem-solving-template/>

> Created and reviewed by Daniel Croft-Bednarski — Head of Continuous
> Improvement, Certified Six Sigma Black Belt. Last updated
> February 4, 2026.

Thanks to Learn Lean Sigma and Daniel Croft-Bednarski for making this template freely
available — this strategy exists because it was possible to work against a real,
well-designed 8D form rather than a made-up example. The template itself is not
distributed here; download it from the link above if you want to try this strategy.

## What it produces

A nested JSON document:

```
{
"doc_meta": { 8D number, dates, initiator, internal/external, ... },
"definitions": { customer, address, location, part no, product name },
"doc_body": { "d1": {...}, "d2": {...}, ... "d7": {...} }
}

Cell values are read by coordinate; text is resolved through the
workbook's shared-string table; Excel serial dates are converted to
ISO dates; checkbox state is read from the workbook's control
properties.

## Known limitations

**This is a v1 and deliberately a demonstration piece, not an
exhaustive parser.**

- **Only the `Blank 8D` sheet is processed** — the main 8D document.
  The template's other sheets (Instructions, Problem Description D2,
  Problem Solving Worksheet D4, Testing Possible Causes D4, Decision
  Making D3 & D5, Risk Analysis, Plan & Problem Prevention) are
  ignored entirely.
- **Coordinates are hardcoded** to this specific template. A modified
  or differently-laid-out 8D form will not map correctly — fields will
  come back empty or wrong rather than raising an error.
- **Checkbox-to-file mapping is hardcoded** for this template's
  control properties. Same caveat applies.
- **`revision_dates`** is read as a single value, though the field
  name suggests a list; multiple revision dates in one cell are not
  split.
- **Merged cells** are read from their top-left coordinate, which is
  where Excel stores the value — correct for this template, but worth
  knowing if you adapt it.

## Requirements

Pluggle, with the `xlsx` optional dependency group installed:

```bash
pip install -e ".[xlsx]"
```

## Usage

```bash
pluggle install-strategy --path learn-lean-sigma-8d-excel-mapper_v1.0.py
# note the uid printed on install

pluggle run \
  --source-type file --source-address /path/to/your-8d-form.xlsx \
  --target-type file --target-address ./8d_output.json \
  --target-format json \
  --transform-strategy <uid>
```

## License

MIT — see the repository
[LICENSE](https://github.com/hsnwhte/pluggle-strategies/blob/main/LICENSE).