---
title: İfade Değerlendirici kaydı | Microsoft Docs
description: İfade değerlendiricinin kendisini hem Windows COM ortamıyla hem de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f928c97961076eaa9d6062d3d812963b1522451b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117936"
---
# <a name="register-an-expression-evaluator"></a>İfade değerlendiriciyi kaydetme
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 İfade değerlendiricisi (EE), kendisini hem Windows COM ortamıyla hem de Visual Studio. Bir EE, hangi varlığın hata ayıklama altyapısı (DE) adres alanı veya Visual Studio adres alanı içine eklemesi için DLL olarak EE.

## <a name="managed-code-expression-evaluator"></a>Yönetilen kod ifadesi değerlendiricisi
 Yönetilen kod EE, kendisini COM ortamına kaydeden bir DLL olan sınıf kitaplığı olarak uygulanır. Bu, genellikle bir VSIP programı çağrısıyla *regpkg.exe.* COM ortamı için kayıt defteri anahtarlarını yazma işlemi otomatik olarak yapılır.

 Main sınıfının bir yöntemi ile işaretlenir ve DLL COM'a kaydedilirken yönteminin <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> çağrıl olacağını belirtir. Genellikle olarak adlandırılan bu kayıt `RegisterClass` yöntemi, DLL'i Visual Studio. Karşılık `UnregisterClass` gelen (ile <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> işaretlenmiş), DLL `RegisterClass` kaldırılırken etkilerini geri alınır.
Aynı kayıt defteri girdileri, bir EE olarak yazılır; Tek fark, işi sizin için yapmak gibi yardımcı `SetEEMetric` bir işlev yoktur. Kayıt ve kayıtsız kayıt işleminin bir örneği aşağıda vemektedir.

### <a name="example"></a>Örnek
 Aşağıdaki işlev, yönetilen bir kodun kendi EE kaydını nasıl geri Visual Studio.

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

## <a name="unmanaged-code-expression-evaluator"></a>Unmanaged code expression evaluator
 EE DLL, hem kendini COM ortamına hem de diğer ortamlara `DllRegisterServer` kaydetmek için Visual Studio.

> [!NOTE]
> EnVSDK\MyCPkgs\MyCEE altındaki VSIP yüklemesinde bulunan *dllentry.cpp* dosyasında MyCEE kodu örnek kayıt defteri kodunu bulabilirsiniz.

### <a name="dll-server-process"></a>DLL sunucusu işlemi
 Dll sunucusunu EE dll sunucusu:

1. Sınıf fabrikasını `CLSID` normal COM kurallarına göre kaydettirmektedir.

2. Aşağıdaki tabloda gösterilen `SetEEMetric` ölçümlerle Visual Studio EE yardımcı işlevini arar. İşlev ve `SetEEMetric` aşağıdaki gibi belirtilen ölçümler *dbgmetric.lib kitaplığının bir parçası.* Ayrıntılar [için bkz. Hata ayıklama için SDK](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) yardımcıları.

    |Metric|Açıklama|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`EE sınıfı fabrikası|
    |`metricName`|Görünen EE olarak dosyanın adı|
    |`metricLanguage`|Değerlendirme için tasarlanmış olan EE adı|
    |`metricEngine`|`GUID`bu hata ayıklama altyapısıyla (DE) EE|

    > [!NOTE]
    > `metricLanguage``GUID`dili adıyla tanımlar, ancak dili `guidLang` `SetEEMetric` seçen bağımsız değişkendir. Derleyici hata ayıklama bilgileri dosyasını üretirken, DE'nin hangi bilgileri kullanmayacaklarını EE `guidLang` yazması gerekir. DE genellikle hata ayıklama bilgileri dosyasında depolanan `GUID` bu dili sembol sağlayıcısına sorar.

3. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudioX.Y altında anahtar oluşturarak Visual Studio ile kaydolr. Burada \\  *X.Y,* Visual Studio sürümüdür.

### <a name="example"></a>Örnek
 Aşağıdaki işlev, bir unmanaged kodun (C++) EE ile kendini nasıl kaydediyor ve Visual Studio.

```cpp
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

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
