---
title: Projedeki başvuruları yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1f2f3c26d89616f083c218c6b11610fe5e329a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651325"
---
# <a name="managing-references-in-a-project"></a>Bir projedeki başvuruları yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir dış bileşene veya bağlı hizmete karşı kod yazmadan önce, projenizin bir başvurusu içermesi gerekir. Başvuru temelde, Visual Studio 'Nun bileşeni veya hizmeti bulması için gereken bilgileri içeren bir proje dosyasındaki giriştir.

 Başvuru eklemek için, Çözüm Gezgini ' deki Başvurular düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. Daha fazla bilgi için bkz. [nasıl yapılır: başvuru Yöneticisi 'Ni kullanarak başvuru ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

 ![Visual C&#43;&#43;bir başvuru ekleme ](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")

 Aşağıdaki bileşen/hizmet türlerine bir başvuru yapabilirsiniz:

- Windows Mağazası uygulama başvuruları

- Sınıf kitaplıkları veya derlemeler .NET Framework

- COM bileşenleri

- Aynı çözümdeki projelerin diğer derlemeleri veya sınıf kitaplıkları

- XML Web hizmetleri

## <a name="windows-store-app-references"></a>Windows Mağazası uygulama başvuruları

### <a name="project-references"></a>Proje Başvuruları
 Windows 10 ' u hedefleyen Evrensel Windows Platformu (UWP) projeleri, çözümdeki diğer UWP projelerine veya [!INCLUDE[win81](../includes/win81-md.md)] Bu projelerin Windows 10 ' da kullanım dışı bırakılan API 'leri kullanmadığından, hedefleyen Windows Mağazası projelerine veya ikili dosyalara başvurular oluşturabilir. Daha fazla bilgi için, bkz. [Windows çalışma zamanı 8 ' den UWP 'e taşıma](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx).

 [!INCLUDE[win81](../includes/win81-md.md)]Projeleri Windows 10 ' a yeniden hedeflemeniz tercih ederseniz bkz. [Visual Studio projelerini taşıma, geçirme ve yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)

### <a name="extension-sdk-references"></a>Uzantı SDK başvuruları
 Visual Basic, C#, C++ ve Evrensel Windows Platformu (UWP) hedefleyen JavaScript Windows Mağazası projeleri, [!INCLUDE[win81](../includes/win81-md.md)] Bu uzantı SDK 'Ları Windows 10 ' da kullanım dışı bırakılan API 'leri kullanmadığından, hedeflenen Uzantı SDK 'lerine başvurabilir. UWP 'yi hedefleyen Windows Mağazası projeleri tarafından başvuranıp başvurulamayacağını öğrenmek için lütfen Uzantı SDK 'Sı satıcı sitesini denetleyin.

 Uygulamanız tarafından başvurulan Uzantı SDK 'sının desteklenmediğini belirlerseniz, aşağıdaki adımları gerçekleştirmeniz gerekir:

1. Hataya neden olan projenin adına bakın. Projenizin hedeflediği platform, proje adının yanında parantez içinde belirtilmiştir. Örneğin, **MyProjectName (Windows 8.1)** , projeniz **MyProjectName** 'in platform sürümünü hedeflediği anlamına gelir [!INCLUDE[win81](../includes/win81-md.md)] .

2. Desteklenmeyen Uzantı SDK 'sına sahip olan satıcının sitesine gidin ve uzantı SDK 'nın sürümünü projenizin hedeflediği platformun sürümü ile uyumlu bağımlılıklarla birlikte yüklemelisiniz.

    > [!NOTE]
    > Bir uzantı SDK 'sının diğer uzantı SDK 'larda bağımlılıklara sahip olup olmadığını bulmanın bir yolu, Visual Studio 'Yu yeniden başlatmak, yeni bir C# Windows Mağazası projesi oluşturmak, projeye sağ tıklayıp **Başvuru Ekle**' yi seçmek Için, **Uzantılar** **alt sekmesine gidip** Uzantı SDK 'sını seçin ve **başvuru Yöneticisi**' nde sağ bölmeye bakın. Bağımlılıklar varsa, burada listelenir.

    > [!IMPORTANT]
    > Projeniz Windows 10 ' u hedefliyorsanız ve önceki adımda yüklenen Uzantı SDK 'nın Microsoft Visual C++ çalışma zamanı paketine bağımlılığı varsa, Windows 10 ile uyumlu Microsoft Visual C++ çalışma zamanı paketinin sürümü v 14.0 ve Visual Studio 2015 ile yüklenir.

3. Önceki adımda yüklediğiniz Uzantı SDK 'sının diğer uzantı SDK 'larına bağımlılıkları varsa, bağımlılıklara sahip olan satıcının sitesine gidin ve projenizin hedeflediği platformun sürümü ile uyumlu olan bu bağımlılıkların sürümlerini yükleyebilirsiniz...

4. Visual Studio 'Yu yeniden başlatın ve uygulamanızı açın.

5. Projede hataya neden olan **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle** ' yi seçin

6. **Windows** sekmesine ve sonra **Uzantılar** alt sekmesine tıklayın ve ardından eski Uzantı SDK 'larının onay kutularının Işaretini kaldırın ve yeni uzantı SDK 'larının onay kutularını işaretleyin. **Tamam**’a tıklayın.

## <a name="adding-a-reference-at-design-time"></a>Tasarım zamanında başvuru ekleme
 Projenizdeki bir derlemeye bir başvuru yaptığınızda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] derlemeyi aşağıdaki konumlarda arar:

- Geçerli proje dizini. (Bu derlemeleri, **tarayıcı** sekmesini kullanarak bulabilirsiniz.)

- Aynı çözümdeki diğer proje dizinleri. (Bu derlemeleri **Projeler** sekmesinde bulabilirsiniz.)

> [!NOTE]
> Tüm projeler mscorlib 'e örtük bir başvuru içerir. Visual Basic projeler için örtük bir başvuru içerir `Microsoft.VisualBasic` .
>
> Visual Studio 'daki tüm projeler `System.Core` , `System.Core` Başvurular listesinden kaldırılsa bile, için örtülü bir başvuru içerir.

## <a name="references-to-shared-components-at-run-time"></a>Çalışma zamanında paylaşılan bileşenlere başvurular
 Çalışma zamanında, bileşenlerin ya projenin çıkış yolunda ya da [genel derleme önbelleğinde](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC) olması gerekir. Proje, bu konumlardan birinde olmayan bir nesneye başvuru içeriyorsa, projeyi oluşturduğunuzda projenin çıkış yoluna başvuruyu kopyalamanız gerekir. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>Özelliği, bu kopyanın yapılıp yapılmayacağını belirtir. Değer **true**ise, projeyi oluşturduğunuzda başvuru proje dizinine kopyalanır. Değer **false**ise, başvuru kopyalanmaz.

 GAC 'de kayıtlı bir özel bileşene başvuru içeren bir uygulama dağıtırsanız, bu ayar ne olursa olsun bileşen uygulamayla birlikte dağıtılmaz <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> . Önceki sürümlerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derlemenin dağıtılmasını sağlamak için bir başvuru üzerinde özelliğini ayarlayabilirsiniz. Şimdi, derlemeyi \bin klasörüne el ile eklemeniz gerekir. Bu, tüm özel kodu scrutlı 'in altına koyar ve alışık olduğunuz özel kodu yayımlama riskini azaltır.

 Varsayılan olarak, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derleme veya bileşen genel derleme önbelleğiyle veya bir çerçeve bileşeni ise, özelliği **false** olarak ayarlanır. Aksi takdirde, değer **true**olarak ayarlanır. Projeden projeye başvurular her zaman **true**olarak ayarlanır.

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>.NET Framework farklı bir sürümünü hedefleyen bir proje veya derlemeye başvurma
 .NET Framework farklı bir sürümünü hedefleyen projelere veya derlemelere başvuran uygulamalar oluşturabilirsiniz. Örneğin, hedefleyen [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] bir derlemeye başvuran bir uygulama oluşturabilirsiniz [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)] . Daha önceki bir sürümünü hedefleyen bir proje oluşturursanız [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , bu projedeki bir başvuruyu [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] veya .NET Framework sürüm 4 ' ü hedefleyen bir proje veya derlemeye ayarlayamazsınız.

 Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="project-to-project-references"></a>Projeden projeye başvurular
 Projeden projeye başvurular, derlemeler içeren projelere referanslardır; **Proje** sekmesini kullanarak bunları oluşturursunuz. Visual Studio, projenin yolunu verildiğinde bir derlemeyi bulabilir.

 Derleme üreten bir projeniz varsa, projeye başvurmanız ve dosya başvurusu kullanmamalısınız (aşağıya bakın). Proje-proje başvurusunun avantajı, derleme sistemindeki projeler arasında bir bağımlılık oluşturmasıdır. Bağımlı proje, başvuran projenin en son derlenmesinden bu yana değiştirilmişse oluşturulur. Bir dosya başvurusu, derleme bağımlılığı oluşturmaz, bu nedenle, bağımlı proje oluşturmadan başvuran projeyi derlemek mümkündür ve başvuru kullanımdan kalkabilir. (Yani, proje projenin daha önce oluşturulmuş bir sürümüne başvurabilir.) Bu, bin dizininde tek bir DLL 'nin gerekli olmasının oluşmasına neden olabilir ve bu mümkün değildir. Bu çakışma oluştuğunda, uyarı şöyle bir ileti görürsünüz [: ' proje ' projesindeki ' dosya ' bağımlılığı, ' File. ' başvurusunun üzerine yazacak olan çalıştırma dizinine kopyalanamıyor](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied.md). Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md) ve [nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Bir projenin .NET Framework hedef sürümü 4,5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3,5 veya 4,0 ise, projeden projeye başvuru yerine bir dosya başvurusu oluşturulur.

## <a name="file-references"></a>Dosya başvuruları
 Dosya başvuruları, Visual Studio projesi bağlamı dışındaki derlemelere doğrudan referanslardır; Bunları, **başvuru Yöneticisi**'nin **tarayıcı** sekmesini kullanarak oluşturursunuz. Yalnızca bir derlemeye veya bileşene sahipseniz ve bunu çıkış olarak oluşturan projeye sahip değilseniz dosya başvurusunu kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Bütünleştirilmiş kodlar Ile](https://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md) derleme [nasıl yapılır: başvuru Yöneticisi 'Ni kullanarak başvuru ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
