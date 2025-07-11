#✅ Amazon Route 53 – DNS Record Types

   ✅ 1. NS (Name Server) Record
   
          Purpose: Tells the internet which name servers are authoritative for your domain.
          
          Example:
          NS → ns-123.awsdns-45.org
          
          Used when you register your domain and point it to AWS Route 53.

✅2. SOA (Start of Authority) Record

            Purpose: Provides metadata about the domain, including:
            
            Primary DNS server
            
            Admin email
            
            Refresh and retry settings
            
            Automatically created by Route 53 for each hosted zone.

✅ 3. A (Address) Record

            Purpose: Maps a domain or subdomain to an IPv4 address.
            
            Example:
            A → 192.0.2.44
            
            4. AAAA (Quad-A) Record
            Purpose: Maps a domain to an IPv6 address.
            
            Example:
            AAAA → 2001:db8::1

✅ 5. CNAME (Canonical Name) Record
          Purpose: Maps a domain to another domain name (not an IP).
          
          Example:
          www.example.com → example.com
          
          Cannot be used for the root domain (e.g., example.com).

✅6. Alias Record

          Purpose: Similar to CNAME, but can be used for the root domain.
          
          Only available in Route 53.
          
          Used to point to AWS resources like:
          
          CloudFront distributions
          
          Elastic Load Balancers
          
          S3 static websites
          
          Example:
          example.com → alias to my-loadbalancer.amazonaws.com
