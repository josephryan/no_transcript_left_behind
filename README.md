# no_transcript_left_behind
use transcriptome to build haplotig-merged assembly

# Experimental code. Not recommended for production, but maybe useful to anyone exploring using transcriptome information to tease apart haplotigs from long-read assemblies.

## NAME

B<no_transcript_left_behind> - use transcriptome to build haplotig-merged assembly 

## AUTHOR

Joseph F. Ryan <joseph.ryan@whitney.ufl.edu>

## SYNOPSIS

no_transcript_left_behind --transcriptome=FASTA --blast=TABBED_BLAST --name=NAME_FOR_OUTPUT [--joindist=INTEGER] [--end_pad=INTEGER] [--max_p_dups=FLOAT] [--ai_cut=INTEGER] [--min_ai=INTEGER] [--max_ai=INTEGER] [--ctg_fa=]

## DESCRIPTION

program does the following: 
(1) build set of contigs (prioritized on length) that have no duplicate transcripts  
(2) BLASTs transcripts vs a db that includes incorporated and non-incorporated contigs  
(3) use alien_index_print_hit to identify transcripts that have better hits in the non-incorporated contigs  
(4) incorporate into the main assembly parts of the non-incorporated contigs that have missing transcripts

## OPTIONS

### --ctg_fa

all genomic contigs

### --transcriptome

(near complete) Transcriptome used to pick contigs

### --blast

BLASTN of transcriptome (--blast) vs. all genomic contigs (--ctg_fa)  
(blastn -query transcriptome -db genomic_contigs -outfmt 6 -max_target_seqs 100 -evalue 0.001)

### --name

NAME for output files

### --joindist

max distance between two matches to merge regions 
when identifying parts of contigs to incorporate in main assembly  

default: 10000

### --end_pad

incorporate up to the end of contig if this many or fewer NTs from end
when identifying parts of contigs to incorporate in main assembly  

default: 2000

### --max_p_dups

percentage of allowable duplications when compiling first set of 
contigs to incorporate into main assembly  

default: 0.0

### --ai_cut

cutoff for alien index when comparing after   

default: 45 


=head1 COPYRIGHT

Copyright (C) 2018 Joseph F. Ryan  

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.  

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.  

