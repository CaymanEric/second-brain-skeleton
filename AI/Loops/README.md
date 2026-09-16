# AI / Loops

Output of Night Shift, a local scheduler that runs small, capped agent jobs
overnight and leaves one morning report here (`YYYY-MM-DD Night Shift.md`:
every run, engine, status, turns, result). Runs on a local model by default and
on Claude only when a loop asks for it. Hard caps on turns, spend, minutes,
runs per night, and concurrency.

Loops may write only inside this folder. Existing notes elsewhere are read,
never changed.
