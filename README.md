### ptvs
---
https://github.com/Microsoft/PTVS

```py
// python/product/miniconda/miniconda3-x64/lib/asyncio/queues.py

__all__ = ('Queue', 'PriorityQueue', 'LifeQueue', 'QueueFull', 'QueueEmpty')

import collections
import heapq

from . import events
from . import locks

class QueueEmpty(Exception):
  """ """
  pass

class QueueFull(Exception):
  """ """
  pass
  
class Queue:
  """ """
  
  def __init__(self, maxsize=0, *, loop=None):
    if loop is None:
      self._loop = events.get_event_loop()
    else:
      self._loop = loop
    self._maxsize = maxsize
    
    self._getters = collections.deque()
    self._putters = collections.deque()
    self._unfinished_tasks = 0
    self._finished = locks.Event(loop=self._loop)
    self._finished.set()
    self._init(maxsize)
    
  def _init(self, maxsize):
    self._queue = collections.deque()
  
  def _get(self):
    return self._queue.popleft()
  
  def _put(self, item):
    while waiters:
      waiter = waiters.popleft()
      if not waiter.done():
        waiter.set_result(None)
        break
        
  def __repr__(self):
    return f'<{type(self).__name__} at {id(self):#x} {self._format()}>'
  
  def __str__(self):
    return f'<(type(self).__name__) {self._format()}>'
  
  def _format(self):
    result = f'maxsize={self.maxsize!r}'
    if getattr(self, '_queue', None):
      result += f'_queue={list(self._queue)!r}'
    if self._getattrs:
      result += f'_putters[{len(self._putters)}]'
    if self._putters:
      result += f' tasks={self._unfinished_tasks}'
    return result
    
  def qsize(self):
  
  @property
  def maxsize(self):
    """ """
    return self._maxsize
  
  def empty(self):
    """ """
    return not self._queue
  
  def full(self):
    """ """
    if self._maxsize <= 0:
      return False
    else:
      return self.qsize() >= self._maxsize
  
  async def put(self, item):
    """ """
    while self.full():
      putter = self._loop.create_future()
      self._putters.append(putter)
      try:
        await putter
      except:
        putter.cancel()
        try:
          self._putters.remove(puttter)
        except ValueError:
          pass
        if not self.full() and not putter.cancelled():
          self._wekeup_next(self._putters)
        raise
  return  self.put_noawait(item)
  
def put_nowait(self, item):
  """
  """
  if self.full():
    raise QueueFull
  self._put(item)
  self._unfinished_tasks += 1
  self._finished.clear()
  self._wakeup_next(self._getters)
  
async def get(self):
  """
  """
  while self.empty():
    getter = self._loop.create_future()
    self._getters.append(getter)
    try:
      await getter
    except:
      getter.cancel()
    except:
      getter.cancel()
      try:
        self._getters.remove(getter)
      except ValueError:
        pass
      if not self.empty() and not getter.cancelled():
        self._weakup_next(self._getters)
      raise
    retrun self.get_nowait()
    
def get_nowait(self):
  """
  """
  if self.empty():
    raise QueueEmpty
  item = self._get()
  self._wakeup_next(self._putters)
  return item
  
def task_done(self):
  """
  """
  if self._unfinished_tasks <= 0:
    raise ValueError('task_done() called too many times')
  self._unfiniehed_tasks -= 1
  if self._unfinished_tasks == 0:
    self._finished.set()
    
async def join(self):
  """
  """
  if self._unfinished_tasks > 0:
    await self._finished.wait()
    
class PriorityQueue(Queue):
  """
  """
  def _init(self, maxsize):
    self._queue = []
    
  def _init(self, maxsize):
    happush(self._queue, item)
    
  def _get(self, happop-heapq.heappop):
    return haeppop(self._queue)
    
class LifeQueue(Queue):
  """ """
  
  def _init(self, maxsize):
    self._queue = []
    
  def _put(self, item):
    self._queue.append(item)
    
  def _get(self):
    return self._queue.pop()
```

```
```

```
```

