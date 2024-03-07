# ROUTING

Định tuyến (Routing) là quá trình lựa chọn và quyết định hướng đi cho gói tin ở bên trong hoặc giữa các **mạng** [[1]](https://www.cisco.com/c/en/us/products/routers/what-is-routing.html).

Router là thiết bị đảm nhiệm vai trò định tuyến này. Các router (bộ định tuyến) tham khảo các bảng định tuyến mà tự chúng xây dựng được để đưa ra quyết định về cách xác định con đường mà gói tin sẽ đi. Bảng định tuyến ghi lại các đường dẫn mà các gói sẽ đi để đến mọi đích mà bộ định tuyến chịu trách nhiệm [[2]](https://www.cloudflare.com/learning/network-layer/what-is-routing/).

Giao thức định tuyến (routing protocol) là giao thức được sử dụng để xác định một đường mạng [[2]](https://www.cloudflare.com/learning/network-layer/what-is-routing/). Một số giao thức định tuyến có thể kể đến là Open Shorted Path First (OSPF), Routing Information Protocol (RIP) và Border Gateway Protocol (BGP) [[2]](https://www.cloudflare.com/learning/network-layer/what-is-routing/). Trong khi đó giao thức OSPF và RIP sẽ được sử dụng trong một vùng mạng tự trị như một tổ chức gọi chung là Interior Gateway Protocol (IGP). Trong khi đó BGP được sử dụng để giao tiếp giữa hai vùng mạng tự trị khác nhau chẳng hạn như ISP, BGP sẽ thuộc External Gateway Protocol [[3]](https://aws.amazon.com/what-is/routing/).

## ROUTE CHOICES

Router chọn interface để đưa gói tin đi ra ngoài dựa vào các cơ chế sau:

- Longest Match.
- [Administrative Distance](./administrative-distance/index.md).

## REFERENCE

[1] <https://www.cisco.com/c/en/us/products/routers/what-is-routing.html>

[2] <https://www.cloudflare.com/learning/network-layer/what-is-routing/>

[3] <https://aws.amazon.com/what-is/routing/>
