# url_shortner


import hashlib

class URLShortener:
    def __init__(self):
        self.url_mapping = {}

    def shorten_url(self, long_url):
        # Generate a hash for the long URL
        url_hash = hashlib.md5(long_url.encode()).hexdigest()[:6]

        # Create a short URL using the hash
        short_url = f"http://short.url/{url_hash}"

        # Store the mapping between short and long URLs
        self.url_mapping[short_url] = long_url

        return short_url

    def expand_url(self, short_url):
        # Retrieve the long URL from the mapping
        return self.url_mapping.get(short_url, "Short URL not found")

# Example usage
url_shortener = URLShortener()
long_url = "http://www.example.com"
short_url = url_shortener.shorten_url(long_url)
print(f"Short URL: {short_url}")

expanded_url = url_shortener.expand_url(short_url)
print(f"Expanded URL: {expanded_url}")
