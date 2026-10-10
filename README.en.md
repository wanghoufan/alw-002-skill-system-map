[简体中文](./README.md) | English

# Skill Capability Map (ALW-002)

A personal map of reusable skills from work, learning, and everyday life. It shows how capabilities are distributed, where they come from, and how they connect across workflows.

**Live site:** [Open the Skill Capability Map](https://wanghoufan.github.io/alw-002-skill-system-map/)

<p><img src="./assets/screenshots/持续改进.png" alt="Continuous improvement: Skill activity heatmap and recent updates" width="100%"></p>

<p><img src="./assets/screenshots/工作与生活的流程地图.png" alt="Workflows: life system and project delivery" width="100%"></p>

<p><img src="./assets/screenshots/能力盘点.png" alt="Capability inventory: Skill statistics, filters, and list" width="100%"></p>

## What the map shows

| Section | What you can explore |
| --- | --- |
| Continuous improvement | A date-based heatmap of recorded Skill changes and recent updates |
| Life and project workflows | How skills connect across everyday management and project delivery |
| Capability inventory | Skills grouped by domain, with source filters for self-built, official, and community / unverified entries, plus search |

Domains include life management, travel, requirements, project collaboration, UI design, content creation, learning and knowledge management, data analysis, automation, testing, deployment, and Skill governance. The live map contains the full domain breakdown and counts.

## Public data snapshot

The public page reflects a data snapshot from **2026-10-10**, with 93 registered Skills. Translations and their English originals are listed separately. Community contributions and entries with unverified sources are labeled “Community / Unverified.”

| Source | Count | Description |
| --- | ---: | --- |
| Self-built | 42 | Original skills and practical experience captured for reuse |
| Official upstream | 24 | Skills from official product or project repositories |
| Community / Unverified | 27 | Community contributions or entries whose source has not been confirmed |

The inventory combines the central `SKILL-REGISTRY.md` with the locally installed Skill Manager list, deduplicated by Skill name. Built-in plugin Skills, ORCA roles, and project-specific practices are excluded from the Skill count. The activity heatmap counts change records in the central registry; it does not measure quality or time spent.

## Quick start

Open the live site above; there is nothing to install or run locally. Select a Skill in a workflow to locate it in the inventory, or use the source filters, domain filters, and search box to find entries.

## Repository files

- `index.html`: the map page
- `assets/skills.json`: public Skill inventory and domains
- `assets/iterations.json`: change records used by the activity heatmap
- `assets/screenshots/`: screenshots shown in this README
