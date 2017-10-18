# ��Դ���������ĵ����ĵ�

## ����ǰ׼��

1. ����Mysoft.Config.Client.DLL��[���ص�ַ](raw/master/�������Ŀͻ���DLL.zip)
2. ���ε���ǰӦִ���������Ŀͻ��˵ĳ�ʼ����Mysoft.Config.Client.ConfigManager.Init()
3. ���õ�ǰվ���Ĭ�ϻ�����ʶ��Ĭ��վ���ʶ��
```xml
<!--�������ģ�������ʶ-->
<add key="configcenter-environmentid" value="product"/>
<!--�������ģ�վ���ʶ-->
<add key="configcenter-appid" value="erp"/>
```
4. ͨ��```Mysoft.Config.Client.ConfigManager```�����������API��

## ���ö�д��ؽӿ�

1. �������Ŀͻ��˳�ʼ��
```c#
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
```

2. ��������ʶ��վ���ʶ��ȡȫ������
```c#
/// <summary>
/// ��ȡָ��������ʶ��ָ��վ���������
/// ����޷���ȡ�����ؿ��ַ���
/// </summary>
/// <param name="envKey">��������</param>
/// <param name="appId">appId</param>
/// <param name="name">����������</param>
/// <returns></returns>
public static string GetSetting(string envKey, string appId, string name);

/// <summary>
/// ��ȡָ��appId�������
/// </summary>
/// <param name="appId">appId</param>
/// <param name="name">����������</param>
/// <returns></returns>
public static string GetSetting(string appId, string name);

/// <summary>
/// ��ȡ��ǰվ��������
/// </summary>
/// <param name="name">����������</param>
/// <returns></returns>
public static string GetSetting(string name);

```


3. ����������
```c#
/// <summary>
/// �������õ�ֵ����������
/// </summary>
/// <param name="name">��������</param>
/// <param name="value">���õ�ֵ</param>
/// <param name="envKey">����Key��Ϊnullʱʹ�õ�ǰ����key</param>
/// <param name="appId">Ӧ�ó����ʶ��Ϊnullʱʹ�õ�ǰվ��key</param>
public static void SetSetting(string name, string value, string envKey = null, string appId = null) 
```

## վ����ؽӿ�

1. ����վ��
```c#
/// <summary>
/// �����÷�������һ��վ����Ϣ
/// </summary>
/// <param name="envKey">������ʶ</param>
/// <param name="siteKey">վ���ʶ</param>
/// <param name="name">վ����ʾ����</param>
/// <param name="url">վ��URL</param>
/// <param name="defineXml">վ�����ö���XML</param>
public static void AddSite(string envKey, string siteKey, string name, string url, string defineXml)
```

2. ��ȡվ���б�
```c#
/// <summary>
/// �����÷����ȡվ���б���Ϣ
/// </summary>
/// <param name="envKey">������ʶ</param>
public static string[] GetSiteList(string envKey)
```

3. ɾ��һ��վ��
```c#
/// <summary>
/// �����÷���ɾ��һ��վ��
/// </summary>
/// <param name="envKey">������ʶ</param>
/// <param name="siteKey">վ���ʶ</param>
public static void DeleteSite(string envKey, string siteKey)
```

4. ��ȡվ������
```c#
/// <summary>
/// ��ȡվ����Ϣ
/// </summary>
/// <param name="envKey">������ʶ������nullĬ�ϵ�ǰ����</param>
/// <param name="siteKey">վ���ʶ</param>
/// <returns></returns>
public static Site GetSiteInfo(string envKey, string siteKey) 

/// <summary>
/// һ��վ��
/// </summary>
[Serializable]
public class Site
{
    /// <summary>
    /// վ��Key
    /// </summary>
    [XmlAttribute("key")]
    [JsonProperty("key")]
    public string Key { get; set; }

    /// <summary>
    /// ����
    /// </summary>
    [XmlAttribute("name")]
    [JsonProperty("name")]
    public string Name { get; set; }

    /// <summary>
    /// վ���ַ
    /// </summary>
    [XmlAttribute("url")]
    [JsonProperty("url")]
    public string Url { get; set; }
}
```



## ������ؽӿ�

1. ���ӻ���
```c#
/// <summary>
/// ���ӻ���
/// </summary>
/// <param name="key"></param>
/// <param name="text"></param>
public static void AddEnvironment(string key, string text);
```

2. ��ȡ�����б�
```c#
/// <summary>
/// ��ȡȫ���Ļ����б�
/// key: ������ʶEnvKey
/// value: ��ʾ����
/// </summary>
/// <returns></returns>
public static List<Service.Models.Environment> GetEnvironmentList()
```

3. ɾ��һ������
```c#
/// <summary>
/// ɾ������
/// </summary>
/// <param name="key"></param>
public static void DelEnvironment(string key)
```
