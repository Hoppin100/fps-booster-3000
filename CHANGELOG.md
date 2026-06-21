# Changelog

## 0.1-BETA

### Core Mod Infrastructure
- Fabric mod entrypoint (main + client + data generator)
- Mod metadata and mixin configuration
- WorldRenderer mixin hook

### Hardware Detection & Auto-Settings
- PC hardware detection (CPU cores, RAM, OS, architecture)
- Hardware tier classification (LOW, MEDIUM, HIGH, ULTRA)
- Auto video settings optimization per tier
- Dynamic view distance adjustment based on FPS
- Auto performance tuning (aggressive/moderate/relaxed modes)
- Adaptive quality engine targeting 120 FPS
- FPS target mode with automatic quality adjustment

### Rendering Optimizations (Culling)
- Frustum culling for entities and block entities
- Occlusion culling with line-of-sight checks
- Entity-type-aware distance culling (items, armor stands, item frames, paintings, villagers)
- Visibility system with priority-ordered render queue

### Rendering Optimizations (LOD)
- Multi-level LOD system (5 levels: FULL to TERRAIN_SILHOUETTE)
- Chunk LOD system with adaptive distance thresholds
- LOD calculator for chunk distance-based detail levels
- LOD renderer with 4 detail levels (full, medium, low, very low)
- LOD mesh data structure
- LOD blend factor calculation
- Greedy mesher (full and fast heightmap-based)

### Rendering Optimizations (Batching & Parallelism)
- Chunk render batching by render layer
- GPU instancing for decorative blocks (grass, torches, fences, flowers)
- Async chunk meshing with thread pool
- Parallel pipeline with 4 dedicated executors (visibility, meshing, LOD, GPU upload)

### Rendering Optimizations (Storage & Caching)
- GPU chunk storage with multi-LOD mesh support and LOD switch cooldown
- Chunk metadata cache (top height, block presence)
- Face visibility cache for block faces
- Light caching with TTL and size limits
- Terrain impostors (16x16 chunk regions at distance)
- Region-based renderer (8x8 chunk regions)

### Object Pooling
- Thread-local collection reuse (ArrayList, HashMap, HashSet)
- Object pool for Vec3d, Box, double arrays
- Advanced object pool for Vector3f, Matrix4f, ByteBuffer

### Resource Management
- Render budget system for chunk uploads, rebuilds, and visibility checks
- Frame time budget tracking (16ms target with over-budget detection)
- Particle budget system with FPS-based limits and pool
- Dynamic mipmap control based on FPS (levels 0-4)
- Dynamic entity shadows based on distance

### Visual Quality Adjustment
- Smart cloud rendering (auto-toggle based on FPS)
- Animated texture throttling (near/far update rates)
- Predictive rendering (movement direction chunk prediction)
- Chunk render prioritizer (distance-based sorting)

### HUD & Debug
- FPS display (color-coded, repositionable)
- Performance profiler overlay (FPS, frame time, budget usage, particles, LOD status)
- Debug overlay toggle

### Server-Side Optimizations
- Block entity tick scheduling (spread across ticks)
- Pathfinding throttling (cooldown every 10 ticks)
- Hopper optimizer (skip empty hoppers)
- Sleeping entities (tick rate by distance to player)
- Villager optimizer (throttle schedules, cache POI searches)
