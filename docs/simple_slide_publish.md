git checkout main
cp Lectures/Lecture1.slides.html /c/temp/

git checkout gh-pages
cp /c/temp/Lecture1.slides.html Lectures/

git add Lectures/Lecture1.slides.html
git commit -m "Add Lecture1 slides"
git push origin gh-pages