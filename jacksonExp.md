Jackson is a quite popular toolkit to convert object and JSON string. In most cases, we just use that for entity we defined. I was confused with the way that just to convert to generics.  
Overlook KV database manpulication code.
```Java 	

// TODO cacheKey
	HashSet<String> getFromCache(String cacheKey) {
		String inCache = null;
		try {
			CollectionType typeRef = 
			 objectMapper.getTypeFactory().constructCollectionType(HashSet.class, String.class);
			
			logger.debug("[CACHE] getFromCache class = {} cacheKey = {}", typeRef, cacheKey);
			inCache = Memcache.getInstance().getString(cacheKey);
			
			if (Strings.isNullOrEmpty(inCache)) {
				return null;
			}
			return objectMapper.readValue(inCache, typeRef);
		} catch (Exception e) {
			logger.debug("[CACHE] fail to deserialize cache for Object:{}. exception={} key={} value=\n{}",
					HashSet.class, e.toString(), cacheKey, inCache);
			return null;
		}
	}

	static String setToCacheByCacheKey(String cacheKey, HashSet<String> entity) {
		if (entity == null) {
			return null;
		}
		logger.debug("[CACHE] setToCacheByCacheKey class={}, cacheKey = {}", entity.getClass().getSimpleName(), cacheKey);
		String value = null;
		try (StringWriter w = new StringWriter()) {
			new ObjectMapper().writeValue(w, entity);
			value = w.getBuffer().toString();
			Memcache.getInstance().setString(cacheKey, value);
			return value;
		} catch (Exception e) {
			logger.debug("[CACHE] fail to serialize object for {}. exception={} key={} value=\n{}",
					e.toString(), entity.getClass().getSimpleName(), cacheKey, value);
			return null;
		}
	}
```
