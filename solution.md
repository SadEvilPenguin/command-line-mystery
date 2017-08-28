
1. started by navigating to crime scene
cd mystery
2. investigated crimscene
cat crimescene
3. pulled out the clues from the report
grep "CLUE" crimescene
Clues:
    1. CLUE: Footage from an ATM security camera is blurry but shows that the perpetrator is a tall male, at least 6.
    2. CLUE: Found a wallet believed to belong to the killer: no ID, just loose change, and membership cards for AAA, Delta SkyMiles, the local library, and the Museum of Bash History. The cards are totally untraceable and have no name, for some reason.
    3. CLUE: Questioned the barista at the local coffee shop. He said a woman left right before they heard the shots. The name on her latte was Annabel, she had blond spiky hair and a New Zealand accent.
4. searched for Annabel in people found 4 - two male
grep "Annabel" people
    1. Annabel Sun	F	26	Hart Place, line 40
    2. Oluwasegun Annabel	M	37	Mattapan Street, line 173
    3. Annabel Church	F	38	Buckingham Place, line 179
    4. Annabel Fuglsang	M	40	Haley Street, line 176
5. Then looked at Buckingham_Place & Hart_Place up to the line for each and found

head -n 179 strets/Buckingham_Place - SEE INTERVIEW #699607
head -n 40 streets/Hart_Place - SEE INTERVIEW #47246024
6. Then looked in interview #699607 and #47246024
cat interviews/interview-699607 

    Interviewed Ms. Church at 2:04 pm.  Witness stated that she did not see anyone she could identify as the shooter, that she ran away as soon as the shots were fired.

    However, she reports seeing the car that fled the scene.  Describes it as a blue Honda, with a license plate that starts with "L337" and ends with "9"

cat interviews/interview-47246024

    Ms. Sun has brown hair and is not from New Zealand.  Not the witness from the cafe.

7. From clues searched vehicles for partial license L337
grep -A 5 "L337" * "9" vehicals and found:

    vehicles:License Plate L337DV9
    vehicles-Make: Honda
    vehicles-Color: Blue
    vehicles-Owner: Joe Germuska
    vehicles-Height: 6'2"
    vehicles-Weight: 164 lbs

    vehicles:License Plate L3375A9
    vehicles-Make: Honda
    vehicles-Color: Blue
    vehicles-Owner: Jeremy Bowers
    vehicles-Height: 6'1"
    vehicles-Weight: 204 lbs

8. From clues checked Joe Germuska, Jeremy Bowers since both are over 6ft. for memberships with AAA, Delta SkyMiles, the local library, and the Museum of Bash History

cd memberships
grep "Joe Germuska" AAA Delta_SkyMiles Terminal_City_Library Museum_of_Bash_History

    AAA:Joe Germuska
    Terminal_City_Library:Joe Germuska

grep "Jeremy Bowers" AAA Delta_SkyMiles Terminal_City_Library Museum_of_Bash_History

AAA:Jeremy Bowers
Delta_SkyMiles:Jeremy Bowers
Terminal_City_Library:Jeremy Bowers
Museum_of_Bash_History:Jeremy Bowers

9. Looks like Jeremy Bowers could be our suspect. Searched for jeremy in people

cd ..
grep "Jeremy Bowers" people

output: Jeremy Bowers	M	34	Dunstable Road, line 284

looked at Dunstable_road at line 284 for interview

head -n 284 streets/Dunstable_Road output: 9620713

looked up interview

cat interviews/interview-9620713
Output: After questioning neighbors, appears that the occupant may have left for a trip recently.

Considered a suspect until proven otherwise, but would have to eliminate other suspects to confirm.

After eliminating the other suspects Jeremy Bowers is our guy!


