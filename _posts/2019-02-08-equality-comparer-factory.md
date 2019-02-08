I'm a big fan of the LINQ Extensions in C#. It provides a functional way of operating on enumerable items. It has been a part of the .NET Framework for a long, long time and is obviously no secret to anyone now.

There are many extensions in LINQ which require something called an `IEqualityComparer`. Eg:

`IEnumerable<TSource> Except<TSource>(this IEnumerable<TSource> first, IEnumerable<TSource> second, IEqualityComparer<TSource> comparer);`

The `IEqualityComparer<T>` is passed in to compare equality of items of type `T`. It can be quite a pain to see that you need to create your own implementation of it to use the extension method. Maybe you'll fall back into a quick and dirty way of acheiving what you want without using that cumbersome `IEqualityComparer<T>` override.

The following is a way of instantiating an `IEqualityComparer<T>` whenever you need it. The factory method takes in a `Func<T, obj>` to select the value you wish to determine equality:

<script src="https://gist.github.com/craigles/4afd9f7125d8fcc746afca74ee0bac60.js"></script>

You can this idea a step further and provide some useful overrides whenever you need it:

<script src="https://gist.github.com/craigles/0b735bb0d09630c9ae37bae3f0af4374.js"></script>

It's a conveniant way to make use of LINQ's extensions for simple equality comparison. I hope you like it.
