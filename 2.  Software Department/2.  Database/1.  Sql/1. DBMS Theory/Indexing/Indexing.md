. Clustering indices are also called primary indices; the term primary index may appear to denote an index on a primary key, but such indices can in fact be built on any search key. The search key of a clustering index is often the primary key, although that is not necessarily so.


<span style="color:rgb(255, 255, 0)">Dense index:</span> In a dense index, an index entry appears for every search-key value in the file. In a dense clustering index, the index record contains the search-key value and a pointer to the first data record with that search-key value. The rest of therecordswiththesamesearch-keyvaluewouldbestoredsequentiallyafterthe first record, since, because the index is a clustering one, records are sorted on the same search key.

