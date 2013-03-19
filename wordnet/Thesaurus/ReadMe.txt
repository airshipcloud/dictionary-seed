A Verbot version of the WordNet English Thesaurus 2.0
Read about WordNet at www.wordnet.princeton.edu


*** Caution ***
The WordNet database contains profanity, words, and phrases that may be offensive to some individuals.

Many of these files are HUGE (from a Verbot point of view) and, depending on the PC, may take several minutes to load.



L I S T  O F  F I L E S :


WordNet_license.txt
==============
The WordNet database license agreement.


Thesaurus_a-z.csv
=============
The full thesaurus (~350,000 rows) in Verbot .CSV compatible format.
The first row contains the following column headings:

Column 1 - Word: The word or phrase being considered.

Column 2 - NumberOfMeanings: The number of meanings for the word or phrase.  One record(row) for each meaning.  The number is duplicated for each meaning.  Many words have more than one meaning.  For example: "cold" has 16 meanings, including frigid, emotionless, and stale.   

Column 3 - POS: Part Of Speech in parentheses, including (noun), (verb), (adj), (adv).

Column 4 through 256 - Term 1, Term3, Term4, ...
One or more words or phrases related to the referenced word or phrase.  The number of terms varies from 1 to 253.  A few WordNet entries include more than 253 terms.  Terms beyond 253 are not included.  Many terms are tagged (generic term), (related term), (similar term), and a few (antonym).  Untagged terms are considered synonyms for that particular meaning of the word. 


Synonym+Similar+Related .CSV and .VSN, 14 files:
Thes_SynSimRel_a-b, _c-e, _f-j, _k-o, _p-r, _s-t, _u-z  in .CSV and .VSN format
========================================================
Words with synonyms and "near" synonyms (tagged similar and related terms) from the thesaurus, split up into spreadsheet manageable pieces, with (tags) removed.  Two columns were added to identify words with multiple meanings:

Column 2 - "Word"_Idx: The word with an _index number attached.

Column 3 - Idx: The word meaning index number.

For example: "cold" has 16 meanings, occupying 16 rows in Thes_SynSimRel_c-e.csv as cold_1, cold_2, cold_3 ... cold_16.  Some "Word"_Idx's are skipped for a few words, usually because a synonym, similar, or related word was not given for that meaning, though it may be a fault in the database or the translation process. 

The words and their "near synonyms" were copied from the .CSV files into associated .VSN synonym files using Macro Scheduler (www.mjtnet.com).  


Thes_Generic_a-b, _c-e, _f-j, _k-o, _p-r, _s-t, _u-z   in .CSV and .VSN format, 14 files
============================================================
Like the "SynSimRel" files, for words and their (generic term) tags.  Words without generic terms are skipped for obvious reasons.


Thes_Antonyms_a-z.csv, .vsn, 2 files:
==========================
Antonyms for 11,700 word_meanings in the database.


Thes_ReverseGeneric.csv, .vsn, 2 files:
==========================
Words with the same (generic term) tag grouped together.  For example: cold (generic term) tag is listed with "chilliness", "cool", "frostiness", "iciness" and "nip".  
29,800 synonym groups total.  Many interesting groups that are worth exploring: use the Editor's Synonym Search/Filter tool.  For example:  yell (generic term) is associated with 57 words, including battle cry, snort, squawk, and wail.


Thesaurus.vkb,.ckb
=============
The Thesaurus knowledgebase returns "similar", generic, and antonyms for synonym groups found in the thesaurus SynSimRel, Generic, and Antonym Synonym files.

Keywords: "thes" , "gen" , "anton" , "idx":

    thes "word" 
    - returns a word (defaults to meaning _1) that is a synonym/similar/related to the entered word.

    gen "word" 
    - returns a generic term (meaning_1) for the entered word.

    anton "word" 
    - returns an antonym (meaning _1) 

Use the idx keyword to lookup other meanings: 

    thes "word" idx "number" 
    - returns a synonym/similar/related term for meaning_"number"

The Verbot returns the synonym output construct, such as ( [word]_[index] ), if no matches are found.

Examples:

User Input:        thes cold
Verbot Output:  A similar or related word would be refrigerating.

User Input:        thes cold idx 2
Verbot Output:  A similar or related word would be insensate.

User Input:         thes cold idx 17
Verbot Output:  A similar or related word would be ( cold_17 ).


WordRelativity Game, 7 Files:
WordRelativity.vkb,.ckb, WordRelativityUnExpanded.vkb,
WordRelativityLevel1.csv, WordRelativityLevel2.csv,WordRelativityLevel3.csv,
WordRelativity.vsn, MyMath.vcm
=======================
WordRelativity.vkb is a word game of 1500 select words from the thesaurus.  Guess the word in 5 tries or less.  A related word is given as a hint, and additional characters in the word are revealed for each try.  There are three levels of difficulty.  Points are gained with each correct answer and the player graduates to the next level when enough points are accumulated.

The game was built from the KB template and .CSV files: WordRelativityUnExpanded.vkb, WordRelativityLevel1.csv, WordRelativityLevel2.csv, and WordRelativityLevel3.csv.  WordRelativity.vsn was assembled from the words in the .CSV files.

MyMath.vcm was written by Matt Palmerlee, and is fully demonstrated in julia_csharp_supplement.vkb.

Example:

Verbot Output:
    Level 1 Try 1 Word 1

    *****
    A verb of 5 characters.
    A related word or phrase:  crow.

User Input:    hollar

Verbot Output:
    Let's give it another try.
    Try 2

    g****
    A verb of 5 characters.
    A related word or phrase:  boast.

User Input:  gloat

Verbot Output:
    gloat is correct.
    Try 2 Winner! 
    Let's try another word ...

    Level 1 Try 1 Word 2

    ****
    A adjective of 4 characters.
    A related word or phrase:  simulated.

