---
title: Eski Dil Hizmetini Geçirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707106"
---
# <a name="migrating-a-legacy-language-service"></a>Eski Dil Hizmetini Geçirme
Projeyi güncelleştirerek ve projeye bir source.extension.vsixmanifest dosyası ekleyerek eski bir dil hizmetini Visual Studio'nun sonraki bir sürümüne geçirebilirsiniz. Visual Studio editörü uyarladığı için dil hizmetinin kendisi eskisi gibi çalışmaya devam edecektir.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Bir dil hizmetini uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Editör ve Dil Hizmeti Uzantıları'na](../../extensibility/editor-and-language-service-extensions.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Visual Studio 2008 Dil Hizmeti Çözümlerini Sonraki Sürüme Geçirmek
 Aşağıdaki adımlar, RegExLanguageService adlı Visual Studio 2008 örneğinin nasıl uyarlanış edilebildiğini göstermektedir. Bu örneği Visual Studio 2008 SDK kurulumunda, *Visual Studio SDK kurulum yolu*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ klasöründe bulabilirsiniz.

> [!IMPORTANT]
> Dil hizmetiniz renkleri tanımlamıyorsa, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` VSPackage'da açıkça ayarlamalısınız:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Visual Studio 2008 dil hizmetini sonraki bir sürüme geçirmek için

1. Visual Studio ve Visual Studio SDK'nın yeni sürümlerini yükleyin. SDK'yı yükleme yolları hakkında daha fazla bilgi için [Visual Studio SDK'yı yükleme ye](../../extensibility/installing-the-visual-studio-sdk.md)bakın.

2. RegExLangServ.csproj dosyasını (Visual Studio'da yüklemeden) edin.

     Microsoft.VsSDK.targets dosyasına başvuran `Import` düğümde, değeri aşağıdaki metinle değiştirin.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Dosyayı kaydedin ve kapatın.

4. RegExLangServ.sln çözümlerini açın.

5. **Tek yönlü yükseltme** penceresi görüntülenir. **Tamam**'a tıklayın.

6. Proje özelliklerini güncelleştirin. **Çözüm Gezgini'ndeki**proje düğümünü seçerek , sağ tıklatarak ve **Özellikleri**seçerek **Project Properties** penceresini açın.

    - **Uygulama** sekmesinde Hedef **çerçeveyi** **4.6.1**olarak değiştirin.

    - Hata **Ayıklama** sekmesinde, **Dış program başlat** kutusunda Visual Studio yükleme yolunu ** \<>\Common7\IDE\devenv.exe yazın.**

         Komut **satırı bağımsız değişkenler** kutusunda, türü /**rootsuffix Exp**.

7. Aşağıdaki referansları güncelleyin:

    - Başvuruyu Microsoft.VisualStudio.Shell.9.0.dll'ye kaldırın ve ardından Microsoft.VisualStudio.Shell.14.0.dll ve Microsoft.VisualStudio.Shell.Immutable.11.0.dll adresine başvuru ekleyin.

    - Başvuruyu Microsoft.VisualStudio.Package.LanguageService.9.0.dll adresine kaldırın ve ardından Microsoft.VisualStudio.Package.LanguageService.14.0.dll adresine bir gönderme ekleyin.

    - Microsoft.VisualStudio.Shell.Interop.10.0.dll adresine başvuru ekleyin.

8. VsPkg.cs dosyasını açın ve özniteliğin `DefaultRegistryRoot` değerini

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Özgün örnek dil hizmetini kaydetmez, bu nedenle VsPkg.cs için aşağıdaki özniteliği eklemeniz gerekir.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Bir source.extension.vsixmanifest dosyası eklemeniz gerekir.

    - Bu dosyayı varolan bir uzantıdan proje dizininize kopyalayın. (Bu dosyayı almak için bir yolu bir VSIX proje oluşturmaktır **(Dosya**altında , **Yeni'yi**tıklatın , sonra **Project'i**tıklatın. Visual Basic veya C# altında **Genişletilebilirlik'i**tıklatın, ardından **VSIX Project'i**seçin .)

    - Dosyayı projenize ekleyin.

    - Dosyanın **Özellikleri'nde,** **Yapı Eylemi'ni** **Yok**olarak ayarlayın.

    - **VSIX Manifest Editor**ile dosyayı açın.

    - Aşağıdaki alanları değiştirin:

    - **ID**: Regexlangserv

    - **Ürün Adı**: Regexlangserv

    - **Açıklama**: Düzenli bir ifade dili hizmeti.

    - **Varlıklar**altında, **Yeni'yi**tıklatın, **Microsoft.VisualStudio.VsPackage** **türü'nü** seçin, **Kaynağı** **geçerli çözümde bir projeye**ayarlayın ve ardından **Projeyi** **RegExLangServ**olarak ayarlayın.

    - Dosyayı kaydedin ve kapatın.

11. Çözümü derleyin. Oluşturulan dosyalar **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\\\RegExLangServ**için dağıtılır.

12. Hata ayıklamaya başla. Visual Studio'nun ikinci bir örneği açıldı.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)
