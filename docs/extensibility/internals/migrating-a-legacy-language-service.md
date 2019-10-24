---
title: Eski dil hizmetini geçirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1027d4b834f1ffdd2289ced2ee5523c20f9d2353
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726691"
---
# <a name="migrating-a-legacy-language-service"></a>Eski Dil Hizmetini Geçirme
Projeyi güncelleştirerek ve projeye bir Source. Extension. valtmanifest dosyası ekleyerek eski bir dil hizmetini Visual Studio 'nun sonraki bir sürümüne geçirebilirsiniz. Dil hizmetinin kendisi, daha önce olduğu gibi çalışmaya devam eder, çünkü Visual Studio Düzenleyicisi tarafından uyum sağlar.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Dil hizmeti uygulama hakkında daha fazla bilgi edinmek için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Visual Studio 2008 dil hizmeti çözümünü sonraki bir sürüme geçirme
 Aşağıdaki adımlarda, RegExLanguageService adlı bir Visual Studio 2008 örneğinin nasıl uyarlandığını gösterilmektedir. Visual Studio *SDK yükleme yolu*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ klasöründe, visual STUDIO 2008 SDK yüklemesinde bu örneği bulabilirsiniz.

> [!IMPORTANT]
> Dil hizmetiniz renk tanımlamıyorsa, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> açıkça VSPackage üzerinde `true` olarak ayarlamanız gerekir:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Visual Studio 2008 dil hizmetini sonraki bir sürüme geçirmek için

1. Visual Studio 'nun daha yeni sürümlerini ve Visual Studio SDK 'sını yükler. SDK 'yı yükleme yolları hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK 'Yı yükleme](../../extensibility/installing-the-visual-studio-sdk.md).

2. RegExLangServ. csproj dosyasını düzenleyin (Visual Studio 'da yüklemeden).

     Microsoft. VsSDK. targets dosyasına başvuran `Import` düğümünde, değeri aşağıdaki metinle değiştirin.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Dosyayı kaydedin ve kapatın.

4. RegExLangServ. sln çözümünü açın.

5. **Tek yönlü yükseltme** penceresi görüntülenir. **Tamam**'a tıklayın.

6. Proje özelliklerini güncelleştirin. **Çözüm Gezgini**proje düğümünü seçip, sağ tıklayıp **Özellikler**' i seçerek **Proje özellikleri** penceresini açın.

    - **Uygulama** sekmesinde **hedef Framework 'ü** **4.6.1**olarak değiştirin.

    - **Hata Ayıkla** sekmesinde, **dış program Başlat** kutusuna **\<Visual Studio yükleme yolu > \Common7\IDE\devenv.exe.** yazın.

         **Komut satırı bağımsız değişkenleri** kutusunda/**rootsuffix exp**yazın.

7. Aşağıdaki başvuruları güncelleştirin:

    - Microsoft. VisualStudio. Shell. 9.0. dll başvurusunu kaldırın, ardından Microsoft. VisualStudio. Shell. 14.0. dll ve Microsoft. VisualStudio. Shell. sabit. 11.0. dll ' ye başvurular ekleyin.

    - Microsoft. VisualStudio. Package. LanguageService. 9.0. dll başvurusunu kaldırın ve ardından Microsoft. VisualStudio. Package. LanguageService. 14.0. dll ' e bir başvuru ekleyin.

    - Microsoft. VisualStudio. Shell. Interop. 10.0. dll için bir başvuru ekleyin.

8. VsPkg.cs dosyasını açın ve `DefaultRegistryRoot` özniteliğinin değerini olarak değiştirin.

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Özgün örnek, dil hizmetini kaydetmez, bu nedenle aşağıdaki özniteliğini VsPkg.cs öğesine eklemeniz gerekir.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Bir Source. Extension. valtmanifest dosyası eklemeniz gerekir.

    - Bu dosyayı varolan bir uzantıdan proje dizininize kopyalayın. (Bu dosyayı almanın bir yolu, bir VSıX projesi oluşturmaktır ( **Dosya**altında **Yeni**' ye ve ardından **Proje**' ye tıklayın. Visual Basic veya C# **genişletilebilirlik**' e ve ardından **VSIX projesi**' ni seçin.)

    - Dosyayı projenize ekleyin.

    - Dosyanın **özelliklerinde**, **derleme eylemini** **none**olarak ayarlayın.

    - Dosyayı **VSIX bildirim Düzenleyicisi**ile açın.

    - Aşağıdaki alanları değiştirin:

    - **Kimlik**: RegExLangServ

    - **Ürün adı**: RegExLangServ

    - **Açıklama**: normal ifade dili hizmeti.

    - **Varlıklar**altında **Yeni**' ye tıklayın, **Microsoft. VisualStudio. VSPackage** **türünü** seçin, **kaynağı** **geçerli çözümdeki bir proje**olarak ayarlayın ve ardından **projeyi** **RegExLangServ**olarak ayarlayın.

    - Dosyayı kaydedin ve kapatın.

11. Çözümü oluşturun. Oluşturulan dosyalar, **%userprofile%\appdata\local\microsoft\visualstudio\14.0exp\extensions\msit\ RegExLangServ\\** 'e dağıtılır.

12. Hata ayıklamayı başlatın. Visual Studio 'nun ikinci bir örneği açıldı.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)