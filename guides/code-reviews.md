# Code Reviews

Code reviews are an integral part of the software development process. They are
not a voluntary act—they are not undertaken because we *choose* to do them—they
are an obligatory, core practice.

A code review is invariably coupled with either a
[pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
or a [merge request](https://docs.gitlab.com/ee/user/project/merge_requests/).
However, do not confuse the mechanics with the purpose: they are a means to an
end. A code review *is* that end.

They are an opportunity discuss, review and—most important of all—*understand*
changes before they are merged into the base branch: mutual comprehension is
key.

## Prerequisites

Remember: [Wheaton's Law](http://www.wheatonslaw.com/) applies at all times.

Before even considering a code review, make sure that you are aware of the
contribution guidelines for the codebase to which you hope to add value. There
may be conventions which dictate things such as:

1. what your branch name should be;
1. if and how work-in-progress is to be marked;
1. whether your code must be rebased from the target branch.

Most importantly, do not even consider requesting a review until your changes
have passed any and all automated processes. Requesting that someone invest time
in reviewing code which fails to meet the minimum standards is a
[sure sign](https://en.wikipedia.org/wiki/Van_Halen#Contract_riders) that
something is likely to have been missed.

Similarly, project maintainers should make sure that the guidelines are clear,
accessible to anyone wishing to contribute and that any automated feedback is
similarly clear and actionable.

## Merge early; merge often

Size matters. Keep 'em small.

A code review is optimal when it leads to fast, clear feedback. The process is
optimal when changes can frequently be integrated into the main codebase. Large
changes are invariably slow to arrive, slow to review and it is often difficult
to assess their success.

## Clarity above all

Keep it brief.

The title and description matter. Explain what has been done and, more
importantly, WHY. Include screenshots, if appropriate.

Don't simply include descriptions of the changes: we can see those, what we
can't is *why*.

## A review is collaborative

Be present. A code-review—whether directly collaborative or asynchronous—is a
mutual act and all involved must give each other and the process the respect
they deserve.

Ideally, a pair-programming workflow allows for more consistent, frequent,
collaborative review of any changes. However, where this is not an optin,
schedule a mutually agreeable time if necessary, or set clear expectations
around availability. Clear and free communication is paramount.

Both the contributor and the reviewer must aim to avoid:

- the fire-and-forget code-review: raise the pull-request, then move on to the
  next feature.
- the drive-by code-review: look at some part of the code, leave comments,
  disappear into the night.

## This is not about you

Personal preference is irrelevant. The standards and conventions of each project
matter but if you can't lint it, you can't dictate it. Leave
[ant-fucking](https://en.wiktionary.org/wiki/mierenneuker) to the machines.

The focus should always be on the code and its relevance to the changes being
implemented.

## This is about you

Someone invested their time on this earth to achieve this: be kind.
