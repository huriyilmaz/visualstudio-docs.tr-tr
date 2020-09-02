---
title: Ifade değerlendiricisi kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3595daa51fddf5c9c027d5643382918d85f83cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837881"
---
# <a name="registering-an-expression-evaluator"></a>İfade Değerlendiricisi Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İfade değerlendirici (EE), hem Windows COM ortamı hem de Visual Studio ile birlikte bir sınıf fabrikası olarak kaydolmalıdır. Bir EE, bir DLL olarak uygulanır, böylece hangi varlığın EE tarafından örneklenebilir olduğuna bağlı olarak hata ayıklama altyapısı (DE) adres alanına veya Visual Studio adres alanına eklenebilir.  
  
## <a name="managed-code-expression-evaluator"></a>Yönetilen kod Ifade değerlendiricisi  
 Yönetilen bir kod EE, kendisini COM ortamıyla kaydeden, genellikle VSıP **regpkg.exe**programı çağrısıyla BAŞLATıLAN bir dll olan sınıf kitaplığı olarak uygulanır. COM ortamı için kayıt defteri anahtarları yazma işleminin gerçek işlemi otomatik olarak gerçekleştirilir.  
  
 Ana sınıfın bir yöntemi ile işaretlenir <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , bu YÖNTEMIN dll com ile kaydedildiğinde çağrılmakta olduğunu gösterir. Genellikle çağrılan bu kayıt yöntemi, `RegisterClass` Visual Studio Ile dll kaydetme görevini gerçekleştirir. Karşılık gelen `UnregisterClass` (ile işaretli <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), dll kaldırıldığında etkilerini geri alır `RegisterClass` .  
  
 Yönetilmeyen kodda yazılmış bir EE için aynı kayıt defteri girişleri yapılır; Tek fark, `SetEEMetric` çalışmayı sizin için yapmak gibi bir yardımcı işlev değildir. Bu kayıt/kayıt silme işleminin bir örneği şöyle görünür:  
  
### <a name="example"></a>Örnek  
 Bu işlev, yönetilen bir kodun, Visual Studio ile kendi kendine nasıl kaydolur ve kaydını silmediğini gösterir.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Yönetilmeyen kod Ifade değerlendiricisi  
 EE DLL, `DllRegisterServer` kendısını com ortamına ve Visual Studio 'ya kaydetmek için işlevi uygular.  
  
> [!NOTE]
> MyCEE kod örneği kayıt defteri kodu, EnVSDK\MyCPkgs\MyCEE. altında VSıP yüklemesinde bulunan dllentry. cpp dosyasında bulunabilir.  
  
### <a name="dll-server-process"></a>DLL sunucusu Işlemi  
 EE kaydedilirken, DLL sunucusu:  
  
1. Sınıf fabrikasını `CLSID` normal com kurallarına göre kaydeder.  
  
2. `SetEEMetric`Aşağıdaki tabloda GÖSTERILEN Ee ölçümlerine Visual Studio ile kaydolmak için yardımcı işlevini çağırır. Bu işlev `SetEEMetric` ve aşağıda belirtilen ölçümler dbgmetric. lib kitaplığının bir parçasıdır. Ayrıntılar için bkz. [hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .  
  
    |Ölçüm|Açıklama|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` EE sınıf fabrikasının|  
    |`metricName`|EE 'ın görüntülenebilen bir dize olarak adı|  
    |`metricLanguage`|EE 'ın değerlendirmek için tasarlandığı dilin adı|  
    |`metricEngine`|`GUID`Bu EE ile çalışan hata ayıklama altyapısının (DE) öğeleri|  
  
    > [!NOTE]
    > , `metricLanguage``GUID` Dili adına göre tanımlar, ancak `guidLang` `SetEEMetric` dilin seçtiği bağımsız değişkendir. Derleyici hata ayıklama bilgileri dosyasını oluşturduğunda, `guidLang` HANGI Ee 'ın kullanılacağını bilmesi için uygun şekilde yazması gerekir. Bu, genellikle sembol sağlayıcısını, `GUID` hata ayıklama bilgileri dosyasında depolanan bu dil için sorar.  
  
3. HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio X. Y altında anahtarlar oluşturarak Visual Studio ile kaydolur; \\ *X.Y*burada *X. Y* , kayıt yapılacak Visual Studio sürümüdür.  
  
### <a name="example"></a>Örnek  
 Bu işlev, yönetilmeyen kod (C++) EE 'ın Visual Studio ile kendisini nasıl kaydedeceğini ve onun kaydını silmediğini gösterir.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR Ifade Değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Hata Ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
