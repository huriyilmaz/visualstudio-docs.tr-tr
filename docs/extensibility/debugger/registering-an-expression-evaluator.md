---
title: Ifade değerlendiricisi kaydetme | Microsoft Docs
description: ifade değerlendiricisi 'nin kendisini hem Windows COM ortamıyla hem de Visual Studio bir sınıf fabrikası olarak kaydetmesi gerektiğini öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634673"
---
# <a name="register-an-expression-evaluator"></a>İfade değerlendiricisi kaydetme
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 ifade değerlendirici (EE), hem Windows hem de COM ortamıyla ve Visual Studio birlikte bir sınıf fabrikası olarak kaydolmalıdır. bir EE, bir DLL olarak ayarlanır. böylece, EE hangi varlığın örneklerinin oluşturulduğu üzerine bağlı olarak, hata ayıklama altyapısı (DE) adres alanına veya Visual Studio adres alanına eklenir.

## <a name="managed-code-expression-evaluator"></a>Yönetilen kod ifade değerlendiricisi
 yönetilen bir kod EE, kendisini COM ortamıyla kaydeden, genellikle vsıp *regpkg.exe* programı çağrısıyla başlatılan bir DLL olan sınıf kitaplığı olarak uygulanır. COM ortamı için kayıt defteri anahtarları yazma işleminin gerçek işlemi otomatik olarak gerçekleştirilir.

 Ana sınıfın bir yöntemi ile işaretlenir <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , bu YÖNTEMIN dll com ile kaydedildiğinde çağrılmakta olduğunu gösterir. Genellikle çağrılan bu kayıt yöntemi, `RegisterClass` DLL 'yi Visual Studio kaydetme görevini gerçekleştirir. Karşılık gelen `UnregisterClass` (ile işaretli <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), dll kaldırıldığında etkilerini geri alır `RegisterClass` .
yönetilmeyen kodda yazılmış bir EE için aynı kayıt defteri girişleri yapılır; Tek fark, `SetEEMetric` çalışmayı sizin için yapmak gibi bir yardımcı işlev değildir. Kayıt ve kayıt silme işleminin bir örneği aşağıda verilmiştir.

### <a name="example"></a>Örnek
 aşağıdaki işlev, EE yönetilen bir kodun Visual Studio ile kendi kaydını nasıl kaydedeceğini gösterir.

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

## <a name="unmanaged-code-expression-evaluator"></a>Yönetilmeyen kod ifade değerlendiricisi
 EE DLL, `DllRegisterServer` kendisini COM ortamına ve Visual Studio kaydetmek için işlevi uygular.

> [!NOTE]
> MyCEE kod örneği kayıt defteri kodunu, EnVSDK\MyCPkgs\MyCEE. altındaki VSıP yüklemesinde bulunan *dllentry. cpp* dosyasında bulabilirsiniz.

### <a name="dll-server-process"></a>DLL sunucusu işlemi
 EE kaydedilirken, DLL sunucusu:

1. Sınıf fabrikasını `CLSID` normal com kurallarına göre kaydeder.

2. `SetEEMetric`aşağıdaki tabloda gösterilen EE ölçümleriyle Visual Studio kaydolmak için yardımcı işlevini çağırır. `SetEEMetric`Aşağıdaki şekilde belirtilen işlev ve ölçümler *dbgmetric. lib* kitaplığının bir parçasıdır. Ayrıntılar için bkz. [hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

    |Metric|Açıklama|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`EE sınıf fabrikası|
    |`metricName`|EE görüntülenebilen bir dize olarak adı|
    |`metricLanguage`|EE değerlendirmek için tasarlanan dilin adı|
    |`metricEngine`|`GUID`Bu EE ile çalışan hata ayıklama altyapısının (DE) öğeleri|

    > [!NOTE]
    > , `metricLanguage``GUID` Dili adına göre tanımlar, ancak `guidLang` `SetEEMetric` dilin seçtiği bağımsız değişkendir. derleyici hata ayıklama bilgileri dosyasını oluşturduğunda, `guidLang` hangi EE kullanacağınızı bilmesi için uygun şekilde yazmalıdır. Bu, genellikle sembol sağlayıcısını, `GUID` hata ayıklama bilgileri dosyasında depolanan bu dil için sorar.

3. x. y HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudioaltında anahtar oluşturarak Visual Studio kaydeder; \\ burada *x. y* , kayıt yapılacak Visual Studio sürümüdür.

### <a name="example"></a>Örnek
 aşağıdaki işlev, yönetilmeyen kod (C++) EE Visual Studio ile kendi kaydını nasıl kaydedeceğini gösterir.

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
