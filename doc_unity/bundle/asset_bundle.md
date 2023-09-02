# 어셋 번들을 로드할때 메모리에 어떻게 올라가는지 확인하고 싶다.

- AssetBundle.LoadFromFile을 할때
- 어셋번들에서 loadAllAssets를 할 때

# 어떤것들을 어떻게 언로드를 해야할지를 확인해 봐야 한다.

var `bundle` = AssetBundle.LoadFromFile(path);
bundle.loadAllAssets();

AssetBundle로드 한 것은  
LoadAllAssets한 것을 언로드 하는것이 아닌

# AssetBundle.LoadFromFile을 했을 때는 메모리가 늘어나지 않는다.

bundle.LoadAllAssets를 한 순가에 메모리에 올라가게 된다.

## loadAllAssets를 하지 않은 녀석을 unload를 하게 되면?

아무문제 없음

## loadAllAssets를 여러번 하면?

문제 없음 메모리가 추가적으로 올라가지 않음

## AssetBundle이 Unload되면 다시 LoadFromFiles를 해주어야 한다.
