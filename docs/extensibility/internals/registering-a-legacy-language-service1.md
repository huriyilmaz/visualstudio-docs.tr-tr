---
title: Eski Dil Hizmeti1 kaydı | Microsoft Docs
description: Kayıt defteri anahtarları ve girdileri ekleyerek bir VSPackage'dan Visual Studio dil hizmetini kaydetme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 35cd10b93a7085654823db94bd7bcc1817012af4b6937b212fd39d568d57bca3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375700"
---
# <a name="registering-a-legacy-language-service-1"></a>Eski dil hizmetini kaydetme 1
Yönetilen paket çerçevesinde (MPF), dil hizmeti bir VSPackage tarafından (bkz. [VSPackage'lar)](../../extensibility/internals/vspackages.md)ve kayıt defteri anahtarları ve girişleri ek olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydediliyor. Bu kayıt işlemi kısmen yükleme sırasında ve kısmen çalışma zamanında yapılır.

## <a name="register-the-language-service-by-using-attributes"></a>Öznitelikleri Kullanarak Dil Hizmetini Kaydetme
 Dil hizmetini kaydetmek için aşağıdaki öznitelikler kullanılır.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Bu öznitelikler aşağıda açıklanmıştır

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
 Bu öznitelik, dil hizmetinizi hizmet olarak kaydedmektedir.

### <a name="example"></a>Örnek

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideServiceAttribute(typeof(TestLanguageService),
                             ServiceName = "Test Language Service")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute
 Bu öznitelik, dil hizmetinizi özellikle bir dil hizmeti olarak kaydedmektedir. Dil hizmetinizin sunduğu özellikleri belirten seçenekler ayarlamanızı sağlar. Örnekte dil hizmetinin sağ alt kümesi ve seçeneklerin bir alt kümesi yer amektedir. Dil hizmeti seçeneklerinin tam kümesi için bkz. <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

### <a name="example"></a>Örnek

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),
                             "Test Language",
                             106,             // resource ID of localized language name
                             CodeSense = true,             // Supports IntelliSense
                             RequestStockColors = false,   // Supplies custom colors
                             EnableCommenting = true,      // Supports commenting out code
                             EnableAsyncCompletion = true  // Supports background parsing
                             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute
 Bu öznitelik, dil hizmetinizi bir dosya uzantısıyla ilişkilendirmektedir. Bu uzantıya sahip bir dosya her yüklendiğinde, herhangi bir projede dil hizmetiniz başlat ve dosyanın içeriğini görüntülemek için kullanılır.

### <a name="example"></a>Örnek

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),
                                       ".Testext")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute
 Bu öznitelik, kod genişletme veya kod parçacığı şablonlarının alınarak bir konum kaydedmektedir. Bu bilgiler Kod Parçacıkları **Tarayıcısı tarafından ve** kaynak dosyaya bir kod parçacığı ekildiğinde düzenleyici tarafından kullanılır.

### <a name="example"></a>Örnek

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageCodeExpansionAttribute(
             typeof(TestLanguageService),
             "Test Language", // Name of language used as registry key.
             106,           // Resource ID of localized name of language service.
             "testlanguage",  // language key used in snippet templates.
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute
 Bu öznitelik, Metin Düzenleyici kategorisi altındaki Seçenekler iletişim **kutusunda görüntülenecek** bir özellik **sayfasını** kaydettirmektedir. Dil hizmetiniz için görüntülenecek her sayfa için bu özniteliklerden birini kullanın. Sayfalarınızı bir ağaç yapısında düzenlemeniz gerekirse, ağacın her düğümünü tanımlamak için ek öznitelikler kullanın.

### <a name="example"></a>Örnek
 Bu örnekte seçenekler ve Girintileme **olmak** için **iki özellik sayfası** ve ikinci özellik sayfasını içeren bir düğüm yer almaktadır.

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Options",      // Registry key name for property page
             "#242",         // Localized name of property page
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Advanced",     // Registry key name for node
             "#243",         // Localized name of node
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             @"Advanced\Indenting",     // Registry key name for property page
             "#244",         // Localized name of property page
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

## <a name="proffer-the-language-service-at-run-time"></a>Çalışma zamanında Dil Hizmeti'nin proffer'ı
 Dil paketiniz yüklendiğinde dil hizmetinizin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hazır olduğunu söylemeniz gerekir. Bunu yapmak için hizmeti proffering. Bu, yönteminde <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yapılır. Buna ek olarak, arka plan ayrıştırmanın gerçek olması için boşta kalma dönemleri sırasında dil hizmetinizi çağıran bir zamanlayıcı başlatmanız gerekir. Bu boşta zamanlayıcı, sınıf aracılığıyla herhangi bir uygulama yaptıysanız belge özelliklerini güncelleştirmek için de <xref:Microsoft.VisualStudio.Package.DocumentProperties> kullanılır. Bir zamanlayıcıyı desteklemek için paketinizin arabirimini uygulaması gerekir (yalnızca yöntemin tam olarak uygulanması gerekir; kalan yöntemler <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> varsayılan değerleri geri getirebilirsiniz).

### <a name="example"></a>Örnek
 Bu örnekte, bir hizmeti temin etmek ve boşta bir zamanlayıcı sağlamak için tipik bir yaklaşım gösterir.

```csharp

using System;
using System.Runtime.InteropServices;
using System.ComponentModel.Design;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.OLE.Interop;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,
        AutoOutlining = true,
        EnableCommenting = true,
        MatchBraces = true,
        ShowMatchingBrace = true)]
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package

    public class TestLanguagePackage : Package, IOleComponent
    {
        private uint m_componentID;

        protected override void Initialize()
        {
            base.Initialize();  // required

            // Proffer the service.
            IServiceContainer serviceContainer = this as IServiceContainer;
            TestLanguageService langService      = new TestLanguageService();
            langService.SetSite(this);
            serviceContainer.AddService(typeof(TestLanguageService),
                                        langService,
                                        true);

            // Register a timer to call our language service during
            // idle periods.
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                       as IOleComponentManager;
            if (m_componentID == 0 && mgr != null)
            {
                OLECRINFO[] crinfo = new OLECRINFO[1];
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
                                              (uint)_OLECADVF.olecadvfRedrawOff |
                                              (uint)_OLECADVF.olecadvfWarningsOff;
                crinfo[0].uIdleTimeInterval = 1000;
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);
            }
        }

        protected override void Dispose(bool disposing)
        {
            if (m_componentID != 0)
            {
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                           as IOleComponentManager;
                if (mgr != null)
                {
                    int hr = mgr.FRevokeComponent(m_componentID);
                }
                m_componentID = 0;
            }

            base.Dispose(disposing);
        }

        #region IOleComponent Members

        public int FDoIdle(uint grfidlef)
        {
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;
            // Use typeof(TestLanguageService) because we need to
            // reference the GUID for our language service.
            LanguageService service = GetService(typeof(TestLanguageService))
                                      as LanguageService;
            if (service != null)
            {
                service.OnIdle(bPeriodic);
            }
            return 0;
        }

        public int FContinueMessageLoop(uint uReason,
                                        IntPtr pvLoopData,
                                        MSG[] pMsgPeeked)
        {
            return 1;
        }

        public int FPreTranslateMessage(MSG[] pMsg)
        {
            return 0;
        }

        public int FQueryTerminate(int fPromptUser)
        {
            return 1;
        }

        public int FReserved1(uint dwReserved,
                              uint message,
                              IntPtr wParam,
                              IntPtr lParam)
        {
            return 1;
        }

        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)
        {
            return IntPtr.Zero;
        }

        public void OnActivationChange(IOleComponent pic,
                                       int fSameComponent,
                                       OLECRINFO[] pcrinfo,
                                       int fHostIsActivating,
                                       OLECHOSTINFO[] pchostinfo,
                                       uint dwReserved)
        {
        }

        public void OnAppActivate(int fActive, uint dwOtherThreadID)
        {
        }

        public void OnEnterState(uint uStateID, int fEnter)
        {
        }

        public void OnLoseActivation()
        {
        }

        public void Terminate()
        {
        }

        #endregion
    }
}
```
