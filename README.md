# leetcode103-zizagLevelOrder



解法一：改变方向，用【：：-1】以及【：：1】来处理

        class Solution:
            def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:

                res = []
                queue = deque([root])
                direction = 1

                if not root:
                    return []

                while queue:
                    level = []
                    for i in range(len(queue)):
                        cur = queue.popleft()
                        level.append(cur.val)
                        if cur.left:
                            queue.append(cur.left)
                        if cur.right:
                            queue.append(cur.right)
                    res.append(level[::direction])
                    direction *= -1
                return res
                
               你看就每一次改变一下方向，每次轮完之后 X -1 即可。
               ⚠️ 注意结尾时候的顺序。这个我比较喜欢的偷懒方式
