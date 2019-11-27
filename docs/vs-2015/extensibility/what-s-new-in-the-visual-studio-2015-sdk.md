---
title: Visual Studio 2015 SDK yenilikler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6735f929f52387f4cb40406d6918894e72bb40d3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299684"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Hangi&#39;'teki Visual Studio 2015 SDK'sı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK, Visual Studio 2015, Visual Studio 2015 güncelleştirme ve Visual Studio 2017 için aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Visual Studio 2017'den itibaren özel Proje ve öğe şablonları için tarama artık gerçekleştirilir. Bunun yerine, uzantı yükleme konumu olarak bu şablonları tanımlamak, şablon bildirim dosyalarını sağlamanız gerekir. VSIX uzantılarınızı güncelleştirmek için Visual Studio 2017'yi kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için bkz. [özel Visual Studio için proje ve öğe şablonları yükseltme 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Şablon bildirim şeması, [Visual Studio şablon bildirimi şema başvurusunda](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)belgelenmiştir.

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK'sı güncelleştirme 1
 Güncelleştirme 1 iyi renk temaları ve Visual Studio Görüntü hizmeti çalışma uzantınız yardımcı olacak araçlar içerir.

 Bu konular [VSSDK yardımcı programları](../extensibility/internals/vssdk-utilities.md) bölümünde bulunur:

- [Renk teması araçları](../extensibility/internals/color-theming-tools.md) , Visual Studio için özel renkler oluşturmanıza ve düzenlemenize yardımcı olur.

- [Görüntü hizmeti araçları](../extensibility/internals/image-service-tools.md) , Visual Studio görüntü bildirim dosyalarıyla çalışmanıza olanak sağlar.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio için Visual Studio SDK eklemek için yeni yol
 Visual Studio 2015'ten başlayarak, Visual Studio SDK'yı ayrı olarak karşıdan yüklemek gerekmez. Bunun yerine, normal yükleme işleminin bir parçası yükleyin ya da daha sonra yüklemek seçebilirsiniz. Bir VSIX çözümüne oluşturun veya açın, Visual Studio, Visual Studio genişletilebilirlik araçları yüklemek için sorar. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Uzantıları oluşturmanın yeni yolu
 Visual Studio 2015 SDK başlayarak, hangi programlama diline bağlı olarak, kullandığınız uzantıları oluşturmak için farklı seçenekler vardır.

### <a name="visual-c-and-visual-basic"></a>Visual C# ve Visual Basic
 C# ve Visual Basic için tam kapsamlı bir VSPackage, menü komutları, araç pencerelerini, düzenleyici sınıflandırıcılar, düzenleyici Kenarlıklar ve düzenleyici kenar boşluğu uzantıları oluşturmanıza imkan tanır ve proje öğesi şablonları yoktur. Tüm standart VSIX projesine ekleyebilirsiniz. Daha fazla bilgi için bkz.:

- [Bir Menü Komutuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Araç Penceresi İçeren Bir Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Düzenleyici Öğesi Şablonuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [VSPackage İçeren Bir Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

     VSPackage Sihirbazı, uzantıları artık C# veya Visual Basic'te oluşturur.

### <a name="c"></a>C++
 C++ için VSPackage Sihirbazı'nı menü komutları, araç pencereleri ve özel düzenleyicileri destekler. **Görsel C++ /genişletilebilirlik**bölümünde **Yeni proje** iletişim kutusunda bulun.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK başvurusu Derlemeleri'nin NuGet aracılığıyla
 Taşınabilirliği artırmak ve genişletilebilirlik projeleri paylaşımı için VS SDK başvurusu derlemeleri'nin NuGet sürümlerini kullanabilirsiniz.  Bunlar, [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) tarafından yayımlanan [NuGet.org](https://www.nuget.org/) üzerinde bulunabilir ve Visual Studio **başvuruları/yönetim NuGet paketleri** iletişim kutusu aracılığıyla projenize veya çözümünüze kolayca eklenebilir. Belirli genişletilebilirlik derlemelerine tek tek başvuruları ekleyebilir veya VS SDK [meta paketini](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)kullanarak bir kerede tüm vs SDK başvuru derlemelerini ekleyebilirsiniz. NuGet hakkında daha fazla bilgi edinmek için bkz. [NuGet 'e genel bakış](https://docs.microsoft.com/nuget/) ve [Iletişim kutusunu kullanarak NuGet paketlerini yönetme](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).

 VS SDK başvurusu derlemeleri'nin NuGet sürümlerini kullandığınızda, başka bir kullanıcı açın ve derleme için VS SDK'sını yükleme gerekmez.  VS SDK derleme araçları ve NuGet başvuru bütünleştirilmiş kodları bilgisayarlarında bu proje için otomatik olarak yüklenir.

 VS SDK'sı öğe şablonları NuGet başvurularını için kullanın ve varsayılan olarak NuGet avantajlarını elde derleme araçları.

> [!NOTE]
> Projeler ile VS SDK yüklü başvuru derlemelerini kullanmaya devam edebilirsiniz (\<Visual Studio yükleme konumu > \ VSSDK\VisualStudioIntegration\Common\Assemblies altında bulunur) ve mevcut genişletilebilirlik projelerinin NuGet paketlerini kullanacak şekilde yükseltilmesi gerekmez.  Proje **başvuruları/başvuru Ekle** iletişim kutusu, vs SDK yüklü başvuru derlemelerini kullanmaya devam eder.
>
> NuGet 'i kullanmak için mevcut projelerinizi değiştirmek isterseniz, bkz. [nasıl yapılır: VSPackages 'ı](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) NuGet paketlerine güncelleştirme hakkında bir bölümü olan Visual Studio 2015 ' a geçirme.

## <a name="light-bulbs"></a>Ampuller
 Uzantı kod yazmayı en heyecan verici yeni yollardan biriyle Roslyn proje tarafından sağlanır. Daha fazla bilgi için bkz. [Roslyn](https://github.com/dotnet/Roslyn).

 Ampuller VSSDK ile birlikte gelen yeni bir özelliktir. Visual Studio Düzenleyicisi'nde kullanılan simgeler, kod yeniden düzenleme işlemleri veya yerleşik kod çözümleyicileri tarafından tanımlanan sorunlar için düzeltmeler gösterecek şekilde genişletmek değildirler. Daha fazla bilgi için bkz. [Izlenecek yol: ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Güncelleştirilmiş kullanıcı deneyimi yönergeleri
 Visual Studio için yeni uzantıları veya özellikler tasarlama? Güncelleştirilmiş ve genişletilmiş [Visual Studio Kullanıcı deneyimi yönergelerine](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)göz atın.  [Renkli belirteçleri](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [yazı tipi boyutlarını](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [iletişim kutusu düzen belirtimlerini](../extensibility/ux-guidelines/layout-for-visual-studio.md)ve yeni kullanıcı arabiriminizi Visual Studio ile sorunsuz bir şekilde tümleştirmeniz için ihtiyacınız olan diğer kılavuzları bulabilirsiniz.
