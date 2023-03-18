---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Ranges
linter-yaml-title-alias: Ranges
date-of-creation: 2023-03-18
mod-date: 2023-03-18
---

# Ranges

## Concept
- *Range*: A set of iterable elements, storing a begin iterator & a sentinel (=last element)
- View: A operation being heavy lazily applied on a range

## Range Types
| Range Type                         | Explanation             | Containers                                        |
| ---------------------------------- | ----------------------- | ------------------------------------------------- |
| `std::ranges::input_range`         | $1\leqslant n$ iterable | `std::unordered_<…>`, `std::forward_list`         |
| `std::ranges::output_range`        | #TODO                   |                                                   |
| `std::ranges::forward_range`       | $1<n$ iterable          |                                                   |
| `std::ranges::bidirectional_range` |                         | `std::(multi)set`, `std::(multi)map`, `std::list` |
| `std::ranges::random_access_range` |                         | `std::deque`                                      |
| `std::ranges::contiguous_range`    |                         | `std::array`, `std::vector`, `std::string`        |

## View Types
- std::all_view, std::views::all // takes all elements
- std::ref_view // takes all elements of another view
- std::filter_view, std::views::filter // takes the elements which satisfies the predicate
- std::transform_view, std::views::transform // transforms each element
- std::take_view, std::views::take // takes the first N elements of another view
- std::take_while_view, std::views::take_while // takes the elements of another view as long as the predicate returns true
- `std::drop_view`, `std::views::drop` // skips the first N elements of another view
- std::drop_while_view, std::views::drop_while // skips the initial elements of another view until the predicate returns false
- std::join_view, std::views::join // joins a view of ranges
- std::split_view, std::views::split // splits a view by using a delimiter
- std::common_view, std::views::common // converts a view into a std::common_range
- std::reverse_view, std::views::reverse // iterates in reverse order
- std::basic_istream_view, std::istream_view // applies operator>> on the view
- std::elements_view, std::views::elements // creates a view on the N-th element of tuples
- std::keys_view, std::views::keys // creates a view on the first element of a pair-like values
- std::values_view, std::views::values // creates a view on the second elements of a pair-like values
---
Sources:
- [Heise](https://www.heise.de/blog/C-20-Die-Ranges-Bibliothek-4661566.html)