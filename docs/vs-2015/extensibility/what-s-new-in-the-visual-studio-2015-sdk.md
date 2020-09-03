---
title: Visual Studio 2015 SDK 'daki yenilikler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917326"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK 'sında ne&#39;yenidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK, Visual Studio 2015, Visual Studio 2015 Updated ve Visual Studio 2017 için aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Visual Studio 2017 ' den başlayarak özel proje ve öğe şablonlarının taranması artık gerçekleştirilmeyecek. Bunun yerine, uzantı Bu şablonların yüklemesinin konumunu tanımlayan şablon bildirim dosyaları sağlamalıdır. VSıX uzantılarınızı güncelleştirmek için Visual Studio 2017 ' i kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için bkz. [özel Visual Studio için proje ve öğe şablonları yükseltme 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Şablon bildirim şeması, [Visual Studio şablon bildirimi şema başvurusunda](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)belgelenmiştir.

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK güncelleştirme 1
 Güncelleştirme 1, uzantınızın renk temaları ve Visual Studio görüntü hizmeti ile iyi çalışmasına yardımcı olacak araçlar içerir.

 Bu konular [VSSDK yardımcı programları](../extensibility/internals/vssdk-utilities.md) bölümünde bulunur:

- [Renk teması araçları](../extensibility/internals/color-theming-tools.md) , Visual Studio için özel renkler oluşturmanıza ve düzenlemenize yardımcı olur.

- [Görüntü hizmeti araçları](../extensibility/internals/image-service-tools.md) , Visual Studio görüntü bildirim dosyalarıyla çalışmanıza olanak sağlar.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio SDK 'sını Visual Studio 'ya eklemenin yeni yolu
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'yı ayrı olarak indirmeniz gerekmez. Bunun yerine, normal yükleme sürecinin bir parçası olarak yükleyebilirsiniz veya daha sonra yüklemeyi tercih edebilirsiniz. Bir VSıX çözümü açtığınızda veya oluşturduğunuzda, Visual Studio sizden Visual Studio Genişletilebilirlik Araçları yüklemenizi isteyecektir. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Uzantı oluşturmanın yeni yolları
 Visual Studio 2015 SDK 'dan başlayarak, kullandığınız programlama diline bağlı olarak uzantı oluşturmaya yönelik farklı seçenekleriniz vardır.

### <a name="visual-c-and-visual-basic"></a>Visual C# ve Visual Basic
 C# ve Visual Basic için, VSPackages, menü komutları, araç pencereleri, düzenleyici sınıflandırıcıları, düzenleyici donnments ve Düzenleyici kenar boşluğu uzantıları oluşturmanıza imkan tanıyan, proje öğesi şablonlarının tam bir yelpazesi vardır. Bunlardan herhangi birini veya tümünü standart VSıX projesine ekleyebilirsiniz. Daha fazla bilgi için bkz.

- [Bir Menü Komutuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Araç Penceresi İçeren Bir Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Düzenleyici Öğesi Şablonuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [VSPackage İçeren Bir Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

     VSPackage Sihirbazı artık C# veya Visual Basic uzantılar oluşturmayacaktır.

### <a name="c"></a>C++
 C++ için, VSPackage Sihirbazı menü komutlarını, araç pencerelerini ve özel düzenleyicilerini destekler. **Visual C++/genişletilebilirlik**bölümünde **Yeni proje** iletişim kutusunda bulun.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>NuGet aracılığıyla VS SDK başvuru derlemeleri
 Daha fazla taşınabilirlik ve genişletilebilirlik projelerinin paylaşılması için VS SDK başvuru derlemelerinin NuGet sürümlerini kullanabilirsiniz.  Bunlar, [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) tarafından yayımlanan [NuGet.org](https://www.nuget.org/) üzerinde bulunabilir ve Visual Studio **başvuruları/yönetim NuGet paketleri** iletişim kutusu aracılığıyla projenize veya çözümünüze kolayca eklenebilir. Belirli genişletilebilirlik derlemelerine tek tek başvuruları ekleyebilir veya VS SDK [meta paketini](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)kullanarak bir kerede tüm vs SDK başvuru derlemelerini ekleyebilirsiniz. NuGet hakkında daha fazla bilgi edinmek için bkz. [NuGet 'e genel bakış](/nuget/) ve [Iletişim kutusunu kullanarak NuGet paketlerini yönetme](/nuget/consume-packages/install-use-packages-visual-studio).

 VS SDK başvuru derlemelerinin NuGet sürümlerini kullandığınızda, başka bir kullanıcının projenizi açmak ve derlemek için VS SDK 'Yı yüklemesi gerekmez.  NuGet başvuru derlemeleri ve VS SDK derleme araçları, bu proje için kendi bilgisayarlarına otomatik olarak yüklenir.

 VS SDK öğe şablonları, varsayılan olarak NuGet avantajlarından yararlanmak için başvuruları ve derleme araçları için NuGet kullanır.

> [!NOTE]
> Projeler ile VS SDK yüklü başvuru derlemelerini kullanmaya devam edebilirsiniz ( \<Visual Studio Install Location> \ VSSDK\VisualStudioIntegration\Common\Assemblies altında bulunur) ve var olan genişletilebilirlik projelerinin NuGet paketlerini kullanacak şekilde yükseltilmesi gerekmez.  Proje **başvuruları/başvuru Ekle** iletişim kutusu, vs SDK yüklü başvuru derlemelerini kullanmaya devam eder.
>
> NuGet 'i kullanmak için mevcut projelerinizi değiştirmek isterseniz, bkz. [nasıl yapılır: VSPackages 'ı](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) NuGet paketlerine güncelleştirme hakkında bir bölümü olan Visual Studio 2015 ' a geçirme.

## <a name="light-bulbs"></a>Hafif bulbs
 Uzantı kodu yazmanın en heyecan verici yeni yöntemlerinden biri Roslyn projesi tarafından sağlanır. Daha fazla bilgi için bkz. [Roslyn](https://github.com/dotnet/Roslyn).

 Hafif bulbs, VSSDK ile birlikte gelen yeni bir özelliktir. Bunlar, Visual Studio Düzenleyicisi 'nde kullanılan ve yerleşik kod Çözümleyicileri tarafından tanımlanan sorunlar için bir kod yeniden düzenleme eylemleri veya düzeltmeler kümesi görüntülenmesini sağlayan simgelerdir. Daha fazla bilgi için bkz. [Izlenecek yol: ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Güncelleştirilmiş Kullanıcı deneyimi yönergeleri
 Visual Studio için yeni uzantılar veya özellikler tasarlansın mı? Güncelleştirilmiş ve genişletilmiş [Visual Studio Kullanıcı deneyimi yönergelerine](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)göz atın.  [Renkli belirteçleri](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [yazı tipi boyutlarını](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [iletişim kutusu düzen belirtimlerini](../extensibility/ux-guidelines/layout-for-visual-studio.md)ve yeni kullanıcı arabiriminizi Visual Studio ile sorunsuz bir şekilde tümleştirmeniz için ihtiyacınız olan diğer kılavuzları bulabilirsiniz.
