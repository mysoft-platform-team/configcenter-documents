# ��Դ���������Ŀ����ĵ�

## �ͻ�������

1. ����Mysoft.Config.Client.DLL
2. ���ε���ǰӦִ���������Ŀͻ��˵ĳ�ʼ����Mysoft.Config.Client.ConfigManager.Init()
3. ���õ�ǰվ���Ĭ�ϻ�����ʶ��Ĭ��վ���ʶ��
```xml
<!--�������ģ�������ʶ-->
<add key="configcenter-environmentid" value="product"/>
<!--�������ģ�վ���ʶ-->
<add key="configcenter-appid" value="erp"/>
```

## �ͻ��˵��ýӿ�

1. �������Ŀͻ��˳�ʼ��
������csharp
/// <summary>
/// ִ�пͻ��˳�ʼ��������ʹ�ô���Ĳ�����
/// </summary>
/// <param name="serviceUri">��������URI</param>
/// <param name="envKey">������ʶ</param>
/// <param name="appId">վ���ʶ</param>
public static void Init(string serviceUri, string envKey, string appId);

/// <summary>
/// ִ�пͻ��˳�ʼ��������ʹ�����õ�ֵ��
/// </summary>
public static void Init();
������

1. ��������ʶ��վ���ʶ��ȡȫ������

2. ��