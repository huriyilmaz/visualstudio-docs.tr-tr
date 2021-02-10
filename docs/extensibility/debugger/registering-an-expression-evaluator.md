---
title: Ifade değerlendiricisi kaydetme | Microsoft Docs
description: İfade değerlendiricisi 'nin kendisini hem Windows COM ortamı hem de Visual Studio ile bir sınıf fabrikası olarak kaydetmesi gerektiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1074e8dea5dfdb05571d3b1aa04e5c411530bb1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961111"
---
# <a name="register-an-expression-evaluator"></a>İfade değerlendiricisi kaydetme
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 İfade değerlendirici (EE), hem Windows COM ortamı hem de Visual Studio ile birlikte bir sınıf fabrikası olarak kaydolmalıdır. Bir EE, bir DLL olarak ayarlanır ve bu sayede, hangi varlığın EE tarafından örnekdiği ile ilgili olarak hata ayıklama altyapısı (DE) adres alanına ya da Visual Studio adres alanına eklenir.

## <a name="managed-code-expression-evaluator"></a>Yönetilen kod ifade değerlendiricisi
 Yönetilen bir kod EE, kendisini COM ortamıyla kaydeden, genellikle VSıP *regpkg.exe* programı çağrısıyla BAŞLATıLAN bir dll olan sınıf kitaplığı olarak uygulanır. COM ortamı için kayıt defteri anahtarları yazma işleminin gerçek işlemi otomatik olarak gerçekleştirilir.

 Ana sınıfın bir yöntemi ile işaretlenir <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , bu YÖNTEMIN dll com ile kaydedildiğinde çağrılmakta olduğunu gösterir. Genellikle çağrılan bu kayıt yöntemi, `RegisterClass` Visual Studio Ile dll kaydetme görevini gerçekleştirir. Karşılık gelen `UnregisterClass` (ile işaretli <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), dll kaldırıldığında etkilerini geri alır `RegisterClass` .
Yönetilmeyen kodda yazılmış bir EE için aynı kayıt defteri girişleri yapılır; Tek fark, `SetEEMetric` çalışmayı sizin için yapmak gibi bir yardımcı işlev değildir. Kayıt ve kayıt silme işleminin bir örneği aşağıda verilmiştir.

### <a name="example"></a>Örnek
 Aşağıdaki işlev, yönetilen bir kodun, Visual Studio ile kendi kendine nasıl kaydolur ve kaydını silmediğini gösterir.

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
 EE DLL, `DllRegisterServer` kendısını com ortamına ve Visual Studio 'ya kaydetmek için işlevi uygular.

> [!NOTE]
> MyCEE kod örneği kayıt defteri kodunu, EnVSDK\MyCPkgs\MyCEE. altındaki VSıP yüklemesinde bulunan *dllentry. cpp* dosyasında bulabilirsiniz.

### <a name="dll-server-process"></a>DLL sunucusu işlemi
 EE kaydedilirken, DLL sunucusu:

1. Sınıf fabrikasını `CLSID` normal com kurallarına göre kaydeder.

2. `SetEEMetric`Aşağıdaki tabloda GÖSTERILEN Ee ölçümlerine Visual Studio ile kaydolmak için yardımcı işlevini çağırır. `SetEEMetric`Aşağıdaki şekilde belirtilen işlev ve ölçümler *dbgmetric. lib* kitaplığının bir parçasıdır. Ayrıntılar için bkz. [hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

    |Metric|Açıklama|
    |------------|-----------------|
    |`metricCLSID`|`CLSID` EE sınıf fabrikasının|
    |`metricName`|EE 'ın görüntülenebilen bir dize olarak adı|
    |`metricLanguage`|EE 'ın değerlendirmek için tasarlandığı dilin adı|
    |`metricEngine`|`GUID`Bu EE ile çalışan hata ayıklama altyapısının (DE) öğeleri|

    > [!NOTE]
    > , `metricLanguage``GUID` Dili adına göre tanımlar, ancak `guidLang` `SetEEMetric` dilin seçtiği bağımsız değişkendir. Derleyici hata ayıklama bilgileri dosyasını oluşturduğunda, `guidLang` HANGI Ee 'ın kullanılacağını bilmesi için uygun şekilde yazması gerekir. Bu, genellikle sembol sağlayıcısını, `GUID` hata ayıklama bilgileri dosyasında depolanan bu dil için sorar.

3. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudiox. Y altında anahtar oluşturarak Visual Studio ile kaydolduktan \\ sonra *x. y* , kayıt yapılacak Visual Studio sürümüdür.

### <a name="example"></a>Örnek
 Aşağıdaki işlev, yönetilmeyen kod (C++) EE 'ın Visual Studio ile kendisini nasıl kaydedeceğini ve onun kaydını silmediğini gösterir.

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
