---
title: find eventual safe states
tags: [leetcode]
categories: leetcode
keywords: LeetCode, leetcode solution in Python3 C++ Java, find-eventual-safe-states solution
description: find eventual safe states LeetCode Solution Explained
cover:
    image: https://scdn.netlify.app/img/leetcode-cover-img.webp
    alt: leetcode-cover-img
    caption: leetcode-cover-img
images: https://scdn.netlify.app/img/leetcode-cover-img.webp
date: 2021-10-04T15:58:26+08:00
lastmod: 2022-03-04T15:58:26+08:00
draft: false
author: Samir Paul
authorLink: https://twitter.com/intent/follow?screen_name=SamirPaulb
license: CC BY 4.0
---


[Discussion Post (created on 29/0/2021 at 14:34)](https://leetcode.com/problems/find-eventual-safe-states/discuss/1040211/DFS-or-Beats-95-or-C%2B%2B)  
<h2>802. Find Eventual Safe States</h2><h3>Medium</h3><hr><div><p>We start at some node in a directed graph, and every turn, we walk along a directed edge of the graph. If we reach a terminal node (that is, it has no outgoing directed edges), we stop.</p>

<p>We define a starting node to be <strong>safe</strong> if we must eventually walk to a terminal node. More specifically, there is a natural number <code>k</code>, so that we must have stopped at a terminal node in less than <code>k</code> steps for <strong>any choice of where to walk</strong>.</p>

<p>Return <em>an array containing all the safe nodes of the graph</em>. The answer should be sorted in <strong>ascending</strong> order.</p>

<p>The directed graph has <code>n</code> nodes with labels from <code>0</code> to <code>n - 1</code>, where <code>n</code> is the length of <code>graph</code>. The graph is given in the following form: <code>graph[i]</code> is a list of labels <code>j</code> such that <code>(i, j)</code> is a directed edge of the graph, going from node <code>i</code> to node <code>j</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="Illustration of graph" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/03/17/picture1.png" style="height: 171px; width: 600px;">
<pre><strong>Input:</strong> graph = [[1,2],[2,3],[5],[0],[5],[],[]]
<strong>Output:</strong> [2,4,5,6]
<strong>Explanation:</strong> The given graph is shown above.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> graph = [[1,2,3,4],[1,2],[3,4],[0,4],[]]
<strong>Output:</strong> [4]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == graph.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= graph[i].legnth &lt;= n</code></li>
	<li><code>graph[i]</code> is sorted in a strictly increasing order.</li>
	<li>The graph may contain self-loops.</li>
	<li>The number of edges in the graph will be in the range <code>[1, 4 * 10<sup>4</sup>]</code>.</li>
</ul>
</div>

---

