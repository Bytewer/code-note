<!--
    File: graph_adjacency_matrix.md
    Created Time: 2024-01-05
    Author: krahets (krahets@163.com)
--->

<!-- [file]{graph_adjacency_matrix}-[class]{graph_adj_mat}-[func]{} -->
<https://pythontutor.com/render.html#code=class%20GraphAdjMat%3A%0A%20%20%20%20%22%22%22%E5%9F%BA%E4%BA%8E%E9%82%BB%E6%8E%A5%E7%9F%A9%E9%98%B5%E5%AE%9E%E7%8E%B0%E7%9A%84%E6%97%A0%E5%90%91%E5%9B%BE%E7%B1%BB%22%22%22%0A%0A%20%20%20%20def%20__init__%28self,%20vertices%3A%20list%5Bint%5D,%20edges%3A%20list%5Blist%5Bint%5D%5D%29%3A%0A%20%20%20%20%20%20%20%20%22%22%22%E6%9E%84%E9%80%A0%E6%96%B9%E6%B3%95%22%22%22%0A%20%20%20%20%20%20%20%20self.vertices%3A%20list%5Bint%5D%20%3D%20%5B%5D%0A%20%20%20%20%20%20%20%20self.adj_mat%3A%20list%5Blist%5Bint%5D%5D%20%3D%20%5B%5D%0A%20%20%20%20%20%20%20%20%23%20%E6%B7%BB%E5%8A%A0%E9%A1%B6%E7%82%B9%0A%20%20%20%20%20%20%20%20for%20val%20in%20vertices%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.add_vertex%28val%29%0A%20%20%20%20%20%20%20%20%23%20%E6%B7%BB%E5%8A%A0%E8%BE%B9%0A%20%20%20%20%20%20%20%20for%20e%20in%20edges%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.add_edge%28e%5B0%5D,%20e%5B1%5D%29%0A%0A%20%20%20%20def%20size%28self%29%20-%3E%20int%3A%0A%20%20%20%20%20%20%20%20%22%22%22%E8%8E%B7%E5%8F%96%E9%A1%B6%E7%82%B9%E6%95%B0%E9%87%8F%22%22%22%0A%20%20%20%20%20%20%20%20return%20len%28self.vertices%29%0A%0A%20%20%20%20def%20add_vertex%28self,%20val%3A%20int%29%3A%0A%20%20%20%20%20%20%20%20%22%22%22%E6%B7%BB%E5%8A%A0%E9%A1%B6%E7%82%B9%22%22%22%0A%20%20%20%20%20%20%20%20n%20%3D%20self.size%28%29%0A%20%20%20%20%20%20%20%20%23%20%E5%90%91%E9%A1%B6%E7%82%B9%E5%88%97%E8%A1%A8%E4%B8%AD%E6%B7%BB%E5%8A%A0%E6%96%B0%E9%A1%B6%E7%82%B9%E7%9A%84%E5%80%BC%0A%20%20%20%20%20%20%20%20self.vertices.append%28val%29%0A%20%20%20%20%20%20%20%20%23%20%E5%9C%A8%E9%82%BB%E6%8E%A5%E7%9F%A9%E9%98%B5%E4%B8%AD%E6%B7%BB%E5%8A%A0%E4%B8%80%E8%A1%8C%0A%20%20%20%20%20%20%20%20new_row%20%3D%20%5B0%5D%20*%20n%0A%20%20%20%20%20%20%20%20self.adj_mat.append%28new_row%29%0A%20%20%20%20%20%20%20%20%23%20%E5%9C%A8%E9%82%BB%E6%8E%A5%E7%9F%A9%E9%98%B5%E4%B8%AD%E6%B7%BB%E5%8A%A0%E4%B8%80%E5%88%97%0A%20%20%20%20%20%20%20%20for%20row%20in%20self.adj_mat%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20row.append%280%29%0A%0A%20%20%20%20def%20remove_vertex%28self,%20index%3A%20int%29%3A%0A%20%20%20%20%20%20%20%20%22%22%22%E5%88%A0%E9%99%A4%E9%A1%B6%E7%82%B9%22%22%22%0A%20%20%20%20%20%20%20%20if%20index%20%3E%3D%20self.size%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20IndexError%28%29%0A%20%20%20%20%20%20%20%20%23%20%E5%9C%A8%E9%A1%B6%E7%82%B9%E5%88%97%E8%A1%A8%E4%B8%AD%E7%A7%BB%E9%99%A4%E7%B4%A2%E5%BC%95%20index%20%E7%9A%84%E9%A1%B6%E7%82%B9%0A%20%20%20%20%20%20%20%20self.vertices.pop%28index%29%0A%20%20%20%20%20%20%20%20%23%20%E5%9C%A8%E9%82%BB%E6%8E%A5%E7%9F%A9%E9%98%B5%E4%B8%AD%E5%88%A0%E9%99%A4%E7%B4%A2%E5%BC%95%20index%20%E7%9A%84%E8%A1%8C%0A%20%20%20%20%20%20%20%20self.adj_mat.pop%28index%29%0A%20%20%20%20%20%20%20%20%23%20%E5%9C%A8%E9%82%BB%E6%8E%A5%E7%9F%A9%E9%98%B5%E4%B8%AD%E5%88%A0%E9%99%A4%E7%B4%A2%E5%BC%95%20index%20%E7%9A%84%E5%88%97%0A%20%20%20%20%20%20%20%20for%20row%20in%20self.adj_mat%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20row.pop%28index%29%0A%0A%20%20%20%20def%20add_edge%28self,%20i%3A%20int,%20j%3A%20int%29%3A%0A%20%20%20%20%20%20%20%20%22%22%22%E6%B7%BB%E5%8A%A0%E8%BE%B9%22%22%22%0A%20%20%20%20%20%20%20%20%23%20%E7%B4%A2%E5%BC%95%E8%B6%8A%E7%95%8C%E4%B8%8E%E7%9B%B8%E7%AD%89%E5%A4%84%E7%90%86%0A%20%20%20%20%20%20%20%20if%20i%20%3C%200%20or%20j%20%3C%200%20or%20i%20%3E%3D%20self.size%28%29%20or%20j%20%3E%3D%20self.size%28%29%20or%20i%20%3D%3D%20j%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20IndexError%28%29%0A%20%20%20%20%20%20%20%20self.adj_mat%5Bi%5D%5Bj%5D%20%3D%201%0A%20%20%20%20%20%20%20%20self.adj_mat%5Bj%5D%5Bi%5D%20%3D%201%0A%0A%20%20%20%20def%20remove_edge%28self,%20i%3A%20int,%20j%3A%20int%29%3A%0A%20%20%20%20%20%20%20%20%22%22%22%E5%88%A0%E9%99%A4%E8%BE%B9%22%22%22%0A%20%20%20%20%20%20%20%20%23%20%E7%B4%A2%E5%BC%95%E8%B6%8A%E7%95%8C%E4%B8%8E%E7%9B%B8%E7%AD%89%E5%A4%84%E7%90%86%0A%20%20%20%20%20%20%20%20if%20i%20%3C%200%20or%20j%20%3C%200%20or%20i%20%3E%3D%20self.size%28%29%20or%20j%20%3E%3D%20self.size%28%29%20or%20i%20%3D%3D%20j%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20raise%20IndexError%28%29%0A%20%20%20%20%20%20%20%20self.adj_mat%5Bi%5D%5Bj%5D%20%3D%200%0A%20%20%20%20%20%20%20%20self.adj_mat%5Bj%5D%5Bi%5D%20%3D%200%0A%0A%0A%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%E6%97%A0%E5%90%91%E5%9B%BE%0A%20%20%20%20vertices%20%3D%20%5B1,%203,%202,%205,%204%5D%0A%20%20%20%20edges%20%3D%20%5B%5B0,%201%5D,%20%5B0,%203%5D,%20%5B1,%202%5D,%20%5B2,%203%5D,%20%5B2,%204%5D,%20%5B3,%204%5D%5D%0A%20%20%20%20graph%20%3D%20GraphAdjMat%28vertices,%20edges%29%0A%0A%20%20%20%20%23%20%E6%B7%BB%E5%8A%A0%E8%BE%B9%0A%20%20%20%20%23%20%E9%A1%B6%E7%82%B9%201,%202%20%E7%9A%84%E7%B4%A2%E5%BC%95%E5%88%86%E5%88%AB%E4%B8%BA%200,%202%0A%20%20%20%20graph.add_edge%280,%202%29%0A%0A%20%20%20%20%23%20%E5%88%A0%E9%99%A4%E8%BE%B9%0A%20%20%20%20%23%20%E9%A1%B6%E7%82%B9%201,%203%20%E7%9A%84%E7%B4%A2%E5%BC%95%E5%88%86%E5%88%AB%E4%B8%BA%200,%201%0A%20%20%20%20graph.remove_edge%280,%201%29%0A%0A%20%20%20%20%23%20%E6%B7%BB%E5%8A%A0%E9%A1%B6%E7%82%B9%0A%20%20%20%20graph.add_vertex%286%29%0A%0A%20%20%20%20%23%20%E5%88%A0%E9%99%A4%E9%A1%B6%E7%82%B9%0A%20%20%20%20%23%20%E9%A1%B6%E7%82%B9%203%20%E7%9A%84%E7%B4%A2%E5%BC%95%E4%B8%BA%201%0A%20%20%20%20graph.remove_vertex%281%29&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false>