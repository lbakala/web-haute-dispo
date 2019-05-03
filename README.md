# web-haute-dispo

Web server High availability

                            +--------+
                            |        | 
                            | Client |      
                            |        |
                            +--------+
                                 |
                                 |              
        +------------------------+--------------------------+
        |                                                   |
        |  +---------+     +------------+     +---------+   |
        |  |         |     |            |     |         |   |
        |  | HAProxy +-----+ Keepalived +-----+ HAProxy |   |
        |  |         |     |            |     |         |   |
        |  +---------+     +------------+     +---------+   |
        |                                                   |
        +------------------------+--------------------------+
                                 |
                                 |
        +------------+-----------+------------+-------------+
        |            |           |            |             |
        |            |           |            |             |
    +---+---+    +---+---+   +---+---+    +---+---+     +---+---+                              
    |       |    |       |   |       |    |       |     |       |
    | Web01 |    | Web02 |   | Web03 |    | Web04 |     | Web05 | 
    |       |    |       |   |       |    |       |     |       |
    +---+---+    +---+---+   +---+---+    +---+---+     +---+---+
        |            |           |            |             |
        +------------+-----------+------------+-------------+
        |              glusterfs -> /var/www                |
        +------------+-----------+------------+-------------+
                     |           |            |
                 +---+---+   +---+---+    +---+---+
                 |       |   |       |    |       |
                 | brick |   | brick |    | brick |
                 |       |   |       |    |       |
                 +-------+   +-------+    +-------+    
