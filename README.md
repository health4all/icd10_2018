About Health4all repo :
Health for all repo is a  collection of information about diseases along the spectrum of ICD`10 codes, from multiple perspectives and disciplines of healthcare and related technology. This is repo is based on github and finds multiple uses towards applications in digital health and advanced technologies like analytics ML, DL and medical robotics.


# icd10_2018

# Some helpful commands
for n in A B C D E F G H I J K L M N O P Q R S T U V W X Y Z; do mkdir -p med-repo/$n; done
cat codes.csv | awk -F, '{tmp = "med-repo/"substr($1,1,1)"/med-proto-"$3".md"; print $0 > tmp; close(tmp)}'

for n in `find med-repo -type f`; do cat $n | awk -F\" '{print "# Category title: "$6"\n\
nAbbreviated description: "$2"\n\nFull description: "$4"\n"}' >> $n ; cat templates/protocol-body.txt >> $n; done

for n in `find med-repo/`; do cat templates/notices.txt >> $n; done

cat repo.txt | awk -F ' ' '{print "rm -rf " $2 $3 $4 "; mkdir -p " $2 $3 $4 "; git clone ssh://git@github.com/" $2 $3 $4 " " $2 $3 $4 "; pushd " $2 $3 $4 "; for n in `find med-repo -type f`; do cp $n `echo $n | cut -d. -f1`." $2 ".md; done; find med-repo -type f | xargs git add; git commit -m \"Added " $2 " suffix\"; git push; popd; rm -rf " $2 $3 $4}'

# Disclaimer 1 :
The information in the document is not meant to be used first point of reference in any of the medical interventions.This is just a compilation of information for academic and knowledge purposes.

# Disclaimer 2 : 
Contributors are alone responsible for avoiding plagiarism or any other adverse effects. They indemnify the editors or originators of this page against any legal, financial or any other type of responsibility.The doc shared and prepared in the Open access will be in accordance with the "Open Access creative commons"  which can be reused. 
