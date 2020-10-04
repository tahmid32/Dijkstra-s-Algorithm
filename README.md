# Dijkstra-s-Algorithm
import math

class Graph():
    def __init__(self, n, c, node_list, connections):
        self.nodes = n
        self.connections = c 
        self.unvisited_list = node_list
        self.connections_dict = connections

    def initialize(self):
        self.unvisited_dict = {k: math.inf for k in self.unvisited_list}
        print(self.unvisited_dict)
        print(self.connections_dict)
    

    def dijkstra(self, src):
        self.visited_dict = {}
        self.unvisited_dict[src] = 0
        #self.current = src
    
        for i in range(self.nodes):
            self.current = min(self.unvisited_dict, key=self.unvisited_dict.get)
            key_list = [key for key in self.connections_dict.keys() if self.current in key]
            for key in key_list:
                lst = key.split(' - ')
                lst.remove(self.current)
                if (self.unvisited_dict[self.current] + self.connections_dict[key]) < self.unvisited_dict[lst[0]]:
                    self.unvisited_dict[lst[0]] = self.unvisited_dict[self.current] + self.connections_dict[key]
                else:
                    self.unvisited_dict[lst[0]] = self.unvisited_dict[lst[0]]
                del self.connections_dict[key]
            self.visited_dict[self.current] = self.unvisited_dict.get(self.current)
            del self.unvisited_dict[self.current]
            
        return self.visited_dict
    
obj = Graph(5, 7, ['A', 'B', 'C', 'D', 'E'], {'A - B': 3, 'B - C': 7, 'C - D': 2, 'D - E': 5, 'C - E': 9, 'B - E': 13, 'A - E': 8})
obj.initialize()
obj.dijkstra('B')
