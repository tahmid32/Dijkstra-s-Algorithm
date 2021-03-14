import math
import copy

class Graph():
    def __init__(self, n, c, nodes_list, connections):
        self.nodes = nself.connections = c 
        self.unvisited_list = nodes_list
        self.connections_dict = connections
    
    def dijkstra(self, src):
        self.unvisited_dict = {k: math.inf for k in self.unvisited_list}
        self.visited_dict = {}
        self.unvisited_dict[src] = 0
        connections_dict_temp = copy.deepcopy(self.connections_dict)
        #self.current = src
        for i in range(self.nodes):
            temp = min(self.unvisited_dict.values()) 
            current = [key for key in self.unvisited_dict if self.unvisited_dict[key] == temp] 
            current = current[0]
            key_list = [key for key in list(connections_dict_temp.keys()) if current in key]
            for key in key_list:
                lst = key.split(' -')
                lst.remove(current)
                if (self.unvisited_dict[current] + connections_dict_temp[key]) < self.unvisited_dict[lst[0]]:
                    self.unvisited_dict[lst[0]] = self.unvisited_dict[current] + connections_dict_temp[key]
                else:
                    self.unvisited_dict[lst[0]] = self.unvisited_dict[lst[0]]
                del connections_dict_temp[key]
            self.visited_dict[current] = self.unvisited_dict.get(current)
            del self.unvisited_dict[current]
        return self.visited_dict

obj = Graph(7, 10, ['A', 'B', 'C', 'D', 'E', 'F', 'G'], {'A -C': 2, 'A -E': 1, 'E -F': 4, 'F -G': 2, 'G -D': 1, 'D -C': 8, 'D -B': 13, 'B -C': 2, 'B -F': 2, 'B -E': 1})
print('Distance of other nodes from source node A:', obj.dijkstra('A'))
print('Distance of other nodes from source node B:', obj.dijkstra('B'))
print('Distance of other nodes from source node C:', obj.dijkstra('C'))
print('Distance of other nodes from source node D:', obj.dijkstra('D'))
print('Distance of other nodes from source node E:', obj.dijkstra('E'))
print('Distance of other nodes from source node F:', obj.dijkstra('F'))
print('Distance of other nodes from source node G:', obj.dijkstra('G'))
