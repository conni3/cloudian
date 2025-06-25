mon, 23 june
- calas meeting
- changed icarus simulation to use verilator instead, which included:
	- writing `sim_main.cpp` for sequential module simulation
	- writing `sim_main_minimal.cpp` for combinational module simulation
	- updating makefile for verilator
	- smoke test for the half adder using verilator (linting and simulation)

Next up:
- update github actions for verilator

tue, 24 june
- making table for accomplishments and future accomplishments for the library
- creating a pipeline for creating issues, updating project, milestones etc from cli:
	- creating a shell script that converts weekly task yml to individual issues
	- creates missing labels and milestones
	- updates to the github project

wed, 25 june
- ta training
- finished github issue creation pipeline
- drafted scaffold_issues and lint_issues scripts

to do: 
- fix linting


thu, 26 june