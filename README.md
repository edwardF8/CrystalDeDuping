## Crystal De-Dupping
Repo for dedupping crystal databases like ICSD, CSD, COD.

### Requirements
Data should be stored in .csv, with chemical name, space group, volume, publication year (maybe).
List of Features:

chemical name: chemical name feature stored in most .cif files
space group: # 1-230 space groups
volume: volume of unit cell, you can also instead have a, b, c, alpha, beta, gamma
publication year: ex: 2006, year that it was published, some databases don't store this

### Steps
1. Using the Processing_Data notebook, make sure your database/databases meet the correct requirements. This might take some playing around with depending on how your own datasets look like, but altogether you should be ready to store the dataset as "CrystalDatabase.csv" with optional columns of:
  'name', 'Local Path', 'Database', 'Publication Year', 'a', 'b','c','alpha','beta','gamma','Volume', 'Bravais Lattice', 'Space Group', 'Numerical Space Group'
  And **required columns** of:
  'name', 'Publication Year', 'Database', 'Volume', 'Space Group', 'Numeric Bravais Lattice'
2. Use the MP_De_Dup.ipynb to De_Dup the dataframe. Use the grapher file to visualize De-Dup vs Dup's Bravais Lattice distribution.
  De-Dup Theology:
    Separates every unique chemical name with more than 1 entry.
      Within this set (dataframe), take the newest entry (by publication year).
        IF there is more than 1 newest, take the entry that is closest to the median Volume of this set.
    Add all other entries to a toRemove dataframe, and filter out the OG dataframe, leaving all entries not in the toRemove dataframe.


## .cif Grabber
If you need to create a .csv with features from a .cif file, use the cifGrapper notebook

You might have to edit the tags in the readFile function depending on what your .cif files look like
