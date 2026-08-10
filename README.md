<img src="https://raw.githubusercontent.com/hsnwhte/pluggle-strategies/main/assets/banner.svg" width="150" alt="Pluggle">

# pluggle-strategies

Curated, reviewed Transform strategies for
[Pluggle](https://github.com/hsnwhte/pluggle). Every strategy here has
been manually reviewed before being added — this isn't an open
marketplace, it's a small, vetted catalog.

## Using a strategy

Install directly by path after downloading:

```bash
pluggle install-strategy --path /path/to/downloaded_strategy.py
```

(Direct `--from-repo <name>` installation is planned — see Pluggle's
`docs/ROADMAP.md`.)

## Catalog

See [`catalog.json`](./catalog.json) for the full list of available
strategies, their descriptions, and file locations. Each strategy has
a matching `.md` file next to its `.py` file with usage notes and
examples.

## Structure
strategies/
├── <strategy_name>.py
├── <strategy_name>.md
...
catalog.json

## Contributing

Have a strategy you think belongs here? Open an issue or a PR. Every
submission is reviewed before merging — this keeps the catalog small
and trustworthy rather than exhaustive.

## License

MIT
