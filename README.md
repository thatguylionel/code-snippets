# code-snippets

When you want to do certain operations in increments (or batches), the use of streams is an option

```
public static <T> Stream<List<T>> batches(List<T> source, int length) {
    if (length <= 0)
        throw new IllegalArgumentException("length = " + length);
    int size = source.size();
    if (size <= 0)
        return Stream.empty();
    int fullChunks = (size - 1) / length;
    return IntStream.range(0, fullChunks + 1).mapToObj(
            n -> source.subList(n * length, n == fullChunks ? size : (n + 1) * length));
}
```  
Then simply call it and do an insane amount of airguitar shredding, because you, my friend, just cranked out solo of monstorous proportions.       

```
batches(fahrerIds, 999).forEach(longs -> {
       // Do action here
       fahrerSpracheList.addAll(someMethodGoesHereAndDoesThings(longListOfLongsOrAnythingReally));
       System.out.println("Iteration " + LocalDateTime.now());
    });


```
