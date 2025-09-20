Unity C#项目，或者纯C#项目，都可以调用此仓库中的dll完成音频转换

主要功能为flac转ogg，mp3转ogg，wav转ogg，并同时重采样，并将声道转换为立体声（2声道）
如果输入输出都是ogg，那就只执行重采样和声道数量转换

使用方式：以Unity项目为例
将本仓库的6个dll放到Assets/Plugins/AudioConvert文件夹下
然后新建一个C#脚本并挂在一个游戏物体上


在C#脚本中写入以下内容：

```c#
[DllImport("AudioConvert.dll", CallingConvention = CallingConvention.Cdecl)]
public static extern bool TryConvertAudio2ogg(string inputPath, string outputPath, int targetSample);

[DllImport("AudioConvert.dll", CallingConvention = CallingConvention.Cdecl)]
public static extern void ConvertAudio2ogg(string inputPath, string outputPath, int targetSample);
```

第一个参数是输入音频路径，第二个参数是输出音频路径，第三个参数是目标采样率

调用示例：

```c#
if (TryConvertAudio2ogg(musicPath, outputPath, 48000))
{
    Debug.Log($"音频转换成功！");
}
else
{ 
    Debug.Log($"音频转换失败！");
}
```



Unity C# projects or pure C# projects can all call the dll in this repository to complete audio conversion. 


The main functions are to convert FLAC to OGG, MP3 to OGG, and WAV to OGG, while simultaneously resampling and converting the channels to stereo (2 channels). If both the input and output are OGG, only resampling and channel count conversion will be performed. 


Usage method: Take a Unity project as an example.
Place the 6 dlls in this repository under the Assets/Plugins/AudioConvert folder.
Then create a new C# script and attach it to a game object. 

Write the following content in the C# script: 
```c#
[DllImport("AudioConvert.dll", CallingConvention = CallingConvention.Cdecl)]
public static extern bool TryConvertAudio2ogg(string inputPath, string outputPath, int targetSample);

[DllImport("AudioConvert.dll", CallingConvention = CallingConvention.Cdecl)]
public static extern void ConvertAudio2ogg(string inputPath, string outputPath, int targetSample);
```

The first parameter is the input audio path, the second parameter is the output audio path, and the third parameter is the target sampling rate. 
Call example: 
```c#
if (TryConvertAudio2ogg(musicPath, outputPath, 48000))
{
Debug.Log($"Audio conversion successful!"); );
}
else
{
Debug.Log($"Audio conversion failed!"); );
}
```