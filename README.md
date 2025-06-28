# DynamicGamma
DynamicGamma


动态Gamma校正引擎

journey
    title Gamma校正开发流程
    section 训练阶段
      Python训练模型 --> ONNX导出 --> 量化压缩
    section 部署阶段
      C#封装DLL --> WPF集成 --> 沙盒测试


      // C#调用ONNX模型
public class GammaCorrector
{
    private InferenceSession _session;
    public GammaCorrector(string modelPath)
    {
        _session = new InferenceSession(modelPath);
    }
    
    public Bitmap Process(Bitmap img)
    {
        var inputs = new List<NamedOnnxValue> { ... };
        using var results = _session.Run(inputs);
        return ConvertToBitmap(results);
    }
}
