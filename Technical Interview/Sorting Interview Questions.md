####  What kind of sorting algorithm you would use in these situations?

- Sort 10 schools around your house by distance.
	-> Small dataset, Insertion Sort would do the job;
- Ebay sorts listings by the current bid amount
	-> Since a bid is an integer in a small range on a fixed length (up to thousands of dollar), use Radix or Counting Sort
- Sort scores on ESPN.
	-> Scores can be of multiple kinds, have floating points etc. So use Quick Sort
- Massive Database(cannot fit all data in memory) needs to sort through past year's user data.
	-> Massive amount of data, so perfomance matters, so Merge Sort to keep in mind worst case scenario.
- Almost sorted Udemy review data needs to update and add 2 new reviews.
	-> Almost sorted data, Insertion Sort works better. 
- Temperature records from the past 50 years in Canada.
	-> If temperature uses precise measurements use Quick Sort. If it's a fixed measurement use Radix or Counting Sort
- Large user name database needs to be sorted. Data is very random.
	->If memory is not an issue Merge Sort.
- You wanna teach sorting to someone
	->Bubble or Selection Sort
