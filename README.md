# Python-05-03

원형 연결 리스트(Node)

```python
class Node():
    def __init__ (self):
        self.data = None
        self.link = None

def printNodes(start):
    current = start
    if current.link == None :
        return
    print(current.data, end = ' ') # 출력되는 글자에 공백을 줌
    while current.link != start:
        current = current.link
        print(current.data, end = ' ') # 출력되는 글자에 공백을 줌
    print()

def insertNode(findData, insertData): 
    global memory, head, current, pre

    if head.data == findData: # 첫번째 노드 삽입
        node = Node()
        node.data = insertData
        node.link = head
        last = head # 마지막 노드를 첫번째 노드로 우선 지정
        while last.link != head : # 마지막 노드를 찾으면 반복 종료
            last = last.link # last를 다음 노드로 변경
        last.link = node # 마지막 노드의 링크에 새 노드 지정
        head = node
        return

def deleteNode(deleteData):
    global memory, head, current, pre

    if head.data == deleteData: # 첫번째 노드 삭제
        current = head
        head = head.link 
        last = head
        while last.link != current : # 마지막 노드를 찾으면 반복 종료
            last = last.link # last를 다음 노드로 변경
        last.link = head # 마지막 노드의 링크에 head가 가리키는 노드 지정
        del(current)
        return
    
    current = head # 첫번째 외 노드 삭제
    while current.link != head:
        pre = current
        current = current.link
        if current.data == deleteData : # 중간 노드를 찾았을 때
            pre.link = current.link
            del(current)
            return

def findNode(findData):
    global memory, head, current, pre

    current = head # 첫번째 외 노드 삭제
    if current.data == findData:
        return current
    while current.link != head:
        current = current.link
        if current.data == findData : # 중간 노드를 찾았을 때
            return current
        return Node()

memory = []
head, current, pre = None, None, None
dataArray = ["다현", "정연", "쯔위", "사나", "지효"]

if __name__ == "__main__":

    node = Node()
    node.data = dataArray[0] # 첫번째 노드
    head = node
    node.link = head
    memory.append(node)

    for data in dataArray[1:]: # 두번째 노드 이후 노드
        pre = node
        node = Node()
        node.data = data
        pre.link = node
        node.link = head
        memory.append(node)

    printNodes(head)

# 리스트 삽입
    insertNode("다현", "화사")
    printNodes(head)

    insertNode("사나", "솔라")
    printNodes(head)

    insertNode("재남", "문별")
    printNodes(head)

# 리스트 삭제
    deleteNode("다현")
    printNodes(head)

    deleteNode("쯔위")
    printNodes(head)

    deleteNode("지효")
    printNodes(head)

    deleteNode("재남")
    printNodes(head)

# 리스트 검색
    fNode = findNode("다현")
    print(fNode.data)

    fNode = findNode("쯔위")
    print(fNode.data)
    
    fNode = findNode("재남")
    print(fNode.data)
```
