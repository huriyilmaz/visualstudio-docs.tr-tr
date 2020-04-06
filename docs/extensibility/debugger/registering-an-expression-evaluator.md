---
title: İfade Değerlendiricisi Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713210"
---
# <a name="register-an-expression-evaluator"></a>İfade değerlendiricisi kaydetme
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 İfade değerlendiricisi (EE) kendisini hem Windows COM ortamına hem de Visual Studio'ya sahip bir sınıf fabrikası olarak kaydetmelidir. EE, hata ayıklama motoruna (DE) adres alanına veya Visual Studio adres alanına hangi varlığın EE'yi anlık olarak verdiğine bağlı olarak enjekte edilebilmek için DLL olarak ayarlanır.

## <a name="managed-code-expression-evaluator"></a>Yönetilen kod ifade değerlendiricisi
 Yönetilen kod EE, genellikle VSIP programına yapılan bir çağrı yla başlatılan, com ortamına kendini kaydeden bir DLL olan Sınıf Kitaplığı olarak uygulanır, *regpkg.exe*. COM ortamı için kayıt defteri anahtarlarını yazma işlemi otomatik olarak işlenir.

 Ana sınıfın bir yöntemi, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>DLL COM'a kaydedilirken yöntemin çağrılacağını belirten bir yöntemle işaretlenir. Genellikle çağrılan `RegisterClass`bu kayıt yöntemi, DLL'yi Visual Studio'ya kaydetme görevini gerçekleştirir. Karşılık `UnregisterClass` gelen (ile <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>işaretlenmiş), DLL `RegisterClass` kaldırıldığında etkilerini geri yapar.
Aynı kayıt defteri girişleri, yönetilmeyen kodla yazılmış bir EE için yapılır; tek fark, sizin için iş yapmak `SetEEMetric` gibi hiçbir yardımcı işlevi olmasıdır. Aşağıda kayıt ve kayıt dışı işlemin bir örneği verilmiştir.

### <a name="example"></a>Örnek
 Aşağıdaki işlev, yönetilen bir kodun EE'nin Visual Studio'ya nasıl kaydolduğunu ve kendisini nasıl kayıt dışı ettiğini gösterir.

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
 EE DLL, Visual `DllRegisterServer` Studio'nun yanı sıra COM ortamına da kaydolmak için işlevi uygular.

> [!NOTE]
> EnVSDK\MyCPkgs\MyCEE altında VSIP yüklemebulunan dosya *dllentry.cpp*, MyCEE kodu örnek kayıt kodu bulabilirsiniz.

### <a name="dll-server-process"></a>DLL sunucu işlemi
 EE'yi kaydederken, DLL sunucusu:

1. Sınıf fabrikasını `CLSID` normal COM kurallarına göre kaydeder.

2. Visual Studio'ya `SetEEMetric` kaydolmak için yardımcı işlevi aşağıdaki tabloda gösterilen EE ölçümlerini çağırır. Aşağıdaki `SetEEMetric` gibi belirtilen işlev ve ölçümler *dbgmetric.lib* kitaplığın bir parçasıdır. Ayrıntılar [için hata ayıklama için SDK yardımcılarına](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) bakın.

    |Ölçüm|Açıklama|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`EE sınıfı fabrikanın|
    |`metricName`|Görüntülenebilir bir dize olarak EE adı|
    |`metricLanguage`|EE'nin değerlendirmek üzere tasarladığı dilin adı|
    |`metricEngine`|`GUID`bu EE ile çalışan hata ayıklama motorlarının (DE)|

    > [!NOTE]
    > Dilin `metricLanguage``GUID` adını tanımlar, ancak dili `guidLang` seçen `SetEEMetric` bağımsız değişkendir. Derleyici hata ayıklama bilgi dosyasını oluşturduğunda, `guidLang` DE'nin hangi EE'yi kullanacağını bilmesi için uygun dosyayı yazmalıdır. DE genellikle hata ayıklama bilgi `GUID`dosyasında depolanan bu dil için sembol sağlayıcısı sorar.

3. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*altında anahtarlar oluşturarak Visual Studio'ya kaydolur ve *X.Y,Visual* Studio'nun kaydolunabileceği sürümdür.

### <a name="example"></a>Örnek
 Aşağıdaki işlev, yönetilmeyen bir kodun (C++) EE'nin Visual Studio'ya nasıl kaydolduğunu ve kendisini nasıl kayıt dışı ettiğini gösterir.

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
