<!--
    File: min_path_sum.md
    Created Time: 2024-01-05
    Author: krahets (krahets@163.com)
--->

<!-- [file]{min_path_sum}-[class]{}-[func]{min_path_sum_dfs} -->
<https://pythontutor.com/render.html#code=from%20math%20import%20inf%0A%0Adef%20min_path_sum_dfs%28grid%3A%20list%5Blist%5Bint%5D%5D,%20i%3A%20int,%20j%3A%20int%29%20-%3E%20int%3A%0A%20%20%20%20%22%22%22%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%EF%BC%9A%E6%9A%B4%E5%8A%9B%E6%90%9C%E7%B4%A2%22%22%22%0A%20%20%20%20%23%20%E8%8B%A5%E4%B8%BA%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%8D%95%E5%85%83%E6%A0%BC%EF%BC%8C%E5%88%99%E7%BB%88%E6%AD%A2%E6%90%9C%E7%B4%A2%0A%20%20%20%20if%20i%20%3D%3D%200%20and%20j%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20return%20grid%5B0%5D%5B0%5D%0A%20%20%20%20%23%20%E8%8B%A5%E8%A1%8C%E5%88%97%E7%B4%A2%E5%BC%95%E8%B6%8A%E7%95%8C%EF%BC%8C%E5%88%99%E8%BF%94%E5%9B%9E%20%2B%E2%88%9E%20%E4%BB%A3%E4%BB%B7%0A%20%20%20%20if%20i%20%3C%200%20or%20j%20%3C%200%3A%0A%20%20%20%20%20%20%20%20return%20inf%0A%20%20%20%20%23%20%E8%AE%A1%E7%AE%97%E4%BB%8E%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%88%B0%20%28i-1,%20j%29%20%E5%92%8C%20%28i,%20j-1%29%20%E7%9A%84%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E4%BB%A3%E4%BB%B7%0A%20%20%20%20up%20%3D%20min_path_sum_dfs%28grid,%20i%20-%201,%20j%29%0A%20%20%20%20left%20%3D%20min_path_sum_dfs%28grid,%20i,%20j%20-%201%29%0A%20%20%20%20%23%20%E8%BF%94%E5%9B%9E%E4%BB%8E%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%88%B0%20%28i,%20j%29%20%E7%9A%84%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E4%BB%A3%E4%BB%B7%0A%20%20%20%20return%20min%28left,%20up%29%20%2B%20grid%5Bi%5D%5Bj%5D%0A%0A%0A%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20grid%20%3D%20%5B%5B1,%203,%201,%205%5D,%20%5B2,%202,%204,%202%5D,%20%5B5,%203,%202,%201%5D,%20%5B4,%203,%205,%202%5D%5D%0A%20%20%20%20n,%20m%20%3D%20len%28grid%29,%20len%28grid%5B0%5D%29%0A%0A%20%20%20%20%23%20%E6%9A%B4%E5%8A%9B%E6%90%9C%E7%B4%A2%0A%20%20%20%20res%20%3D%20min_path_sum_dfs%28grid,%20n%20-%201,%20m%20-%201%29%0A%20%20%20%20print%28f%22%E4%BB%8E%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%88%B0%E5%8F%B3%E4%B8%8B%E8%A7%92%E7%9A%84%E5%81%9A%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%E4%B8%BA%20%7Bres%7D%22%29&cumulative=false&curInstr=6&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false>

<!-- [file]{min_path_sum}-[class]{}-[func]{min_path_sum_dfs_mem} -->
<https://pythontutor.com/render.html#code=from%20math%20import%20inf%0A%0Adef%20min_path_sum_dfs_mem%28%0A%20%20%20%20grid%3A%20list%5Blist%5Bint%5D%5D,%20mem%3A%20list%5Blist%5Bint%5D%5D,%20i%3A%20int,%20j%3A%20int%0A%29%20-%3E%20int%3A%0A%20%20%20%20%22%22%22%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%EF%BC%9A%E8%AE%B0%E5%BF%86%E5%8C%96%E6%90%9C%E7%B4%A2%22%22%22%0A%20%20%20%20%23%20%E8%8B%A5%E4%B8%BA%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%8D%95%E5%85%83%E6%A0%BC%EF%BC%8C%E5%88%99%E7%BB%88%E6%AD%A2%E6%90%9C%E7%B4%A2%0A%20%20%20%20if%20i%20%3D%3D%200%20and%20j%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20return%20grid%5B0%5D%5B0%5D%0A%20%20%20%20%23%20%E8%8B%A5%E8%A1%8C%E5%88%97%E7%B4%A2%E5%BC%95%E8%B6%8A%E7%95%8C%EF%BC%8C%E5%88%99%E8%BF%94%E5%9B%9E%20%2B%E2%88%9E%20%E4%BB%A3%E4%BB%B7%0A%20%20%20%20if%20i%20%3C%200%20or%20j%20%3C%200%3A%0A%20%20%20%20%20%20%20%20return%20inf%0A%20%20%20%20%23%20%E8%8B%A5%E5%B7%B2%E6%9C%89%E8%AE%B0%E5%BD%95%EF%BC%8C%E5%88%99%E7%9B%B4%E6%8E%A5%E8%BF%94%E5%9B%9E%0A%20%20%20%20if%20mem%5Bi%5D%5Bj%5D%20!%3D%20-1%3A%0A%20%20%20%20%20%20%20%20return%20mem%5Bi%5D%5Bj%5D%0A%20%20%20%20%23%20%E5%B7%A6%E8%BE%B9%E5%92%8C%E4%B8%8A%E8%BE%B9%E5%8D%95%E5%85%83%E6%A0%BC%E7%9A%84%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E4%BB%A3%E4%BB%B7%0A%20%20%20%20up%20%3D%20min_path_sum_dfs_mem%28grid,%20mem,%20i%20-%201,%20j%29%0A%20%20%20%20left%20%3D%20min_path_sum_dfs_mem%28grid,%20mem,%20i,%20j%20-%201%29%0A%20%20%20%20%23%20%E8%AE%B0%E5%BD%95%E5%B9%B6%E8%BF%94%E5%9B%9E%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%88%B0%20%28i,%20j%29%20%E7%9A%84%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E4%BB%A3%E4%BB%B7%0A%20%20%20%20mem%5Bi%5D%5Bj%5D%20%3D%20min%28left,%20up%29%20%2B%20grid%5Bi%5D%5Bj%5D%0A%20%20%20%20return%20mem%5Bi%5D%5Bj%5D%0A%0A%0A%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20grid%20%3D%20%5B%5B1,%203,%201,%205%5D,%20%5B2,%202,%204,%202%5D,%20%5B5,%203,%202,%201%5D,%20%5B4,%203,%205,%202%5D%5D%0A%20%20%20%20n,%20m%20%3D%20len%28grid%29,%20len%28grid%5B0%5D%29%0A%0A%20%20%20%23%20%E8%AE%B0%E5%BF%86%E5%8C%96%E6%90%9C%E7%B4%A2%0A%20%20%20%20mem%20%3D%20%5B%5B-1%5D%20*%20m%20for%20_%20in%20range%28n%29%5D%0A%20%20%20%20res%20%3D%20min_path_sum_dfs_mem%28grid,%20mem,%20n%20-%201,%20m%20-%201%29%0A%20%20%20%20print%28f%22%E4%BB%8E%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%88%B0%E5%8F%B3%E4%B8%8B%E8%A7%92%E7%9A%84%E5%81%9A%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%E4%B8%BA%20%7Bres%7D%22%29&cumulative=false&curInstr=16&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false>

<!-- [file]{min_path_sum}-[class]{}-[func]{min_path_sum_dp} -->
<https://pythontutor.com/render.html#code=from%20math%20import%20inf%0A%0Adef%20min_path_sum_dp%28grid%3A%20list%5Blist%5Bint%5D%5D%29%20-%3E%20int%3A%0A%20%20%20%20%22%22%22%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%EF%BC%9A%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%22%22%22%0A%20%20%20%20n,%20m%20%3D%20len%28grid%29,%20len%28grid%5B0%5D%29%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%20dp%20%E8%A1%A8%0A%20%20%20%20dp%20%3D%20%5B%5B0%5D%20*%20m%20for%20_%20in%20range%28n%29%5D%0A%20%20%20%20dp%5B0%5D%5B0%5D%20%3D%20grid%5B0%5D%5B0%5D%0A%20%20%20%20%23%20%E7%8A%B6%E6%80%81%E8%BD%AC%E7%A7%BB%EF%BC%9A%E9%A6%96%E8%A1%8C%0A%20%20%20%20for%20j%20in%20range%281,%20m%29%3A%0A%20%20%20%20%20%20%20%20dp%5B0%5D%5Bj%5D%20%3D%20dp%5B0%5D%5Bj%20-%201%5D%20%2B%20grid%5B0%5D%5Bj%5D%0A%20%20%20%20%23%20%E7%8A%B6%E6%80%81%E8%BD%AC%E7%A7%BB%EF%BC%9A%E9%A6%96%E5%88%97%0A%20%20%20%20for%20i%20in%20range%281,%20n%29%3A%0A%20%20%20%20%20%20%20%20dp%5Bi%5D%5B0%5D%20%3D%20dp%5Bi%20-%201%5D%5B0%5D%20%2B%20grid%5Bi%5D%5B0%5D%0A%20%20%20%20%23%20%E7%8A%B6%E6%80%81%E8%BD%AC%E7%A7%BB%EF%BC%9A%E5%85%B6%E4%BD%99%E8%A1%8C%E5%92%8C%E5%88%97%0A%20%20%20%20for%20i%20in%20range%281,%20n%29%3A%0A%20%20%20%20%20%20%20%20for%20j%20in%20range%281,%20m%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20dp%5Bi%5D%5Bj%5D%20%3D%20min%28dp%5Bi%5D%5Bj%20-%201%5D,%20dp%5Bi%20-%201%5D%5Bj%5D%29%20%2B%20grid%5Bi%5D%5Bj%5D%0A%20%20%20%20return%20dp%5Bn%20-%201%5D%5Bm%20-%201%5D%0A%0A%0A%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20grid%20%3D%20%5B%5B1,%203,%201,%205%5D,%20%5B2,%202,%204,%202%5D,%20%5B5,%203,%202,%201%5D,%20%5B4,%203,%205,%202%5D%5D%0A%20%20%20%20n,%20m%20%3D%20len%28grid%29,%20len%28grid%5B0%5D%29%0A%0A%20%20%20%20%23%20%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%0A%20%20%20%20res%20%3D%20min_path_sum_dp%28grid%29%0A%20%20%20%20print%28f%22%E4%BB%8E%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%88%B0%E5%8F%B3%E4%B8%8B%E8%A7%92%E7%9A%84%E5%81%9A%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%E4%B8%BA%20%7Bres%7D%22%29&cumulative=false&curInstr=6&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false>

<!-- [file]{min_path_sum}-[class]{}-[func]{min_path_sum_dp_comp} -->
<https://pythontutor.com/render.html#code=from%20math%20import%20inf%0A%0Adef%20min_path_sum_dp_comp%28grid%3A%20list%5Blist%5Bint%5D%5D%29%20-%3E%20int%3A%0A%20%20%20%20%22%22%22%E6%9C%80%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%EF%BC%9A%E7%A9%BA%E9%97%B4%E4%BC%98%E5%8C%96%E5%90%8E%E7%9A%84%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%22%22%22%0A%20%20%20%20n,%20m%20%3D%20len%28grid%29,%20len%28grid%5B0%5D%29%0A%20%20%20%20%23%20%E5%88%9D%E5%A7%8B%E5%8C%96%20dp%20%E8%A1%A8%0A%20%20%20%20dp%20%3D%20%5B0%5D%20*%20m%0A%20%20%20%20%23%20%E7%8A%B6%E6%80%81%E8%BD%AC%E7%A7%BB%EF%BC%9A%E9%A6%96%E8%A1%8C%0A%20%20%20%20dp%5B0%5D%20%3D%20grid%5B0%5D%5B0%5D%0A%20%20%20%20for%20j%20in%20range%281,%20m%29%3A%0A%20%20%20%20%20%20%20%20dp%5Bj%5D%20%3D%20dp%5Bj%20-%201%5D%20%2B%20grid%5B0%5D%5Bj%5D%0A%20%20%20%20%23%20%E7%8A%B6%E6%80%81%E8%BD%AC%E7%A7%BB%EF%BC%9A%E5%85%B6%E4%BD%99%E8%A1%8C%0A%20%20%20%20for%20i%20in%20range%281,%20n%29%3A%0A%20%20%20%20%20%20%20%20%23%20%E7%8A%B6%E6%80%81%E8%BD%AC%E7%A7%BB%EF%BC%9A%E9%A6%96%E5%88%97%0A%20%20%20%20%20%20%20%20dp%5B0%5D%20%3D%20dp%5B0%5D%20%2B%20grid%5Bi%5D%5B0%5D%0A%20%20%20%20%20%20%20%20%23%20%E7%8A%B6%E6%80%81%E8%BD%AC%E7%A7%BB%EF%BC%9A%E5%85%B6%E4%BD%99%E5%88%97%0A%20%20%20%20%20%20%20%20for%20j%20in%20range%281,%20m%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20dp%5Bj%5D%20%3D%20min%28dp%5Bj%20-%201%5D,%20dp%5Bj%5D%29%20%2B%20grid%5Bi%5D%5Bj%5D%0A%20%20%20%20return%20dp%5Bm%20-%201%5D%0A%0A%0A%22%22%22Driver%20Code%22%22%22%0Aif%20__name__%20%3D%3D%20%22__main__%22%3A%0A%20%20%20%20grid%20%3D%20%5B%5B1,%203,%201,%205%5D,%20%5B2,%202,%204,%202%5D,%20%5B5,%203,%202,%201%5D,%20%5B4,%203,%205,%202%5D%5D%0A%20%20%20%20n,%20m%20%3D%20len%28grid%29,%20len%28grid%5B0%5D%29%0A%0A%20%20%20%20%23%20%E7%A9%BA%E9%97%B4%E4%BC%98%E5%8C%96%E5%90%8E%E7%9A%84%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%0A%20%20%20%20res%20%3D%20min_path_sum_dp_comp%28grid%29%0A%20%20%20%20print%28f%22%E4%BB%8E%E5%B7%A6%E4%B8%8A%E8%A7%92%E5%88%B0%E5%8F%B3%E4%B8%8B%E8%A7%92%E7%9A%84%E5%81%9A%E5%B0%8F%E8%B7%AF%E5%BE%84%E5%92%8C%E4%B8%BA%20%7Bres%7D%22%29&cumulative=false&curInstr=6&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false>