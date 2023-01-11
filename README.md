# README

Running discrete phylogeographies on large datasets

Link to full SOP: https://docs.google.com/document/d/1mTwKrQ6UCP75_5ncyiS2RjE4tdn5LJOTCve_cbH0j7c/edit#

## Short version:

1. Get ML topology with IQTree

`iqtree -fast -m hky -s alignment.fasta -nt AUTO -o outgroup.taxon -czb`

1b. Prune outgroup

`jclusterfunk prune -i <input_file> -taxa <id> -output <output_file>`


2. Scale roughly in time with Treetime (optional but recommended for runtime efficiency)

`treetime --sequence-length <length_of_alignment> --tree <input.nwk> --dates <dates.csv> --keep-root `

3. Scale properly in time with thorney beast 

Use thorney_beast.xml as a template

3b. Grab last tree from that file

X = 2n+9 where n is the number of taxa

[on Command line]

~~~
head -X trees_file.tree > top_section.txt

tail -2 trees_file.tree > last_tree.txt

cat top_section.txt last_tree.txt > best_tree.txt
~~~

4. Run DTA
Use DTA_template.xml as a template


