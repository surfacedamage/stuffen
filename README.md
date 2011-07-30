# Description
This script will easily scan through a directory of photos and copy them to a new location organized by year based on the photo EXIF date created.

### So, this:

  - Birthday at Aunt Susies
    - photo1.jpg
    - photo2.jpg
    - The cat blows out candles
      - cat_photo1.jpg
      - cat_photo2.jpg
  - Driving a boat like a boss wearing a cat hat
    - on the boat.jpg
    - description.txt
  - 2011
    - 2011-06-14 - An old properly organized album
      - crashing a boat.jpg


### Becomes this:

  - 2011
    - 2011-06-14 - An old properly organized album
      - crashing a boat.jpg
    - 2011-05-13 - Birthday at Aunt Susies
      - photo1.jpg
      - photo2.jpg
      - The cat blows out candles
        - cat_photo1.jpg
        - cat_photo2.jpg
  - 2008
    - 2008-03-30 - Driving a boat like a boss wearing a cat hat
      - on the boat.jpg
      - description.txt


# Usage:
* gem install bundler
* bundle install
* rake stuffen:copy['/mypath/to/photos', '/mypath/to/new/location']


# Limitations 
* only handles jpg files
* only first photo in directory will be used for date
