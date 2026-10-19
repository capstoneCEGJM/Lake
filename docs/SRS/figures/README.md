# SRS figure sources

The PNGs in `docs/SRS/` are rendered from these files. Re-render after editing and
commit both the source and the PNG.

| Source | Output | Render with |
| --- | --- | --- |
| `context_diagram.dot` | `../context_diagram.png` | `dot -Tpng context_diagram.dot -o ../context_diagram.png` |
| `goal_model.dot` | `../goal_model.png` | `neato -Tpng goal_model.dot -o ../goal_model.png` (run from this folder; it reads `cloud.png`) |
| `g5_usecase.puml` | `../g5_usecase.png` | `plantuml -tpng -o .. g5_usecase.puml` |
| `requirement_dependencies.puml` | `../requirement_dependencies.png` | `PLANTUML_LIMIT_SIZE=8192 plantuml -tpng -o .. requirement_dependencies.puml` |

`goal_model.dot` uses the goal-model notation from SFWRENG 3RA3 (actors, hard goals, soft
goals, plans, resources, AND decomposition, +/- contributions). Node positions are pinned
in inches with `pos="x,y!"`, so move a node by editing its coordinates. `cloud.png` is the
soft-goal shape, since Graphviz has no cloud shape.

`requirement_dependencies.puml` has one box per detailed requirement (blue FR, yellow NFR
and NFR.E, pink SR). A solid arrow goes from a requirement to one it "Depends on" in
`SRS.tex`; a dashed arrow means "is satisfied by" or "is related to". When a requirement
or one of its links changes, update the diagram source and the dependency table
(`../requirement_dependencies_table.tex`) to match.

Graphviz and PlantUML are installed with `brew install graphviz plantuml`.
