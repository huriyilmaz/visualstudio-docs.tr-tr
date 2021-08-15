---
title: Bir projedeki başvuruları yönetme
description: Bir projedeki dış bileşenlere ve bağlı hizmetlere yönelik başvuruları yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3bffcdece76db2da6e33d84877d2577f1f6fe4c09f735bd360198bed799f4a4e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121318609"
---
# <a name="manage-references-in-a-project"></a>Bir projedeki başvuruları yönetme

Bir dış bileşene veya bağlı hizmete karşı kod yazmadan önce, projenizin bir başvurusu içermesi gerekir. başvuru, temel olarak Visual Studio bir proje dosyasında bileşeni veya hizmeti bulmak için gereken bilgileri içeren bir giriştir.

Başvuru eklemek için, **Çözüm Gezgini** ' deki **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. Ayrıca, proje düğümüne sağ tıklayıp başvuru **Ekle**' yi seçebilirsiniz  >  . Daha fazla bilgi için bkz. [nasıl yapılır: başvuruları ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Visual C&#43;&#43; bir başvuru ekleme](../ide/media/vs2015_cpp_add_reference.png)

Aşağıdaki bileşen ve hizmet türlerine bir başvuru ekleyebilirsiniz:

- .NET sınıf kitaplıkları veya derlemeleri

- UWP uygulamaları

- COM bileşenleri

- Aynı çözümdeki projelerin diğer derlemeleri veya sınıf kitaplıkları

- Paylaşılan projeler

- XML Web hizmetleri

## <a name="uwp-app-references"></a>UWP uygulama başvuruları

### <a name="project-references"></a>Proje başvuruları

Evrensel Windows Platformu (UWP) projeleri, bu projelerin Windows 10 kullanım dışı bırakılmış apı 'leri kullanmadığından, çözümdeki diğer UWP projelerine veya Windows 8.1 projelere veya ikili dosyalara başvurular oluşturabilir. daha fazla bilgi için, bkz. [Windows Çalışma Zamanı 8 ' den UWP 'e taşıma](/windows/uwp/porting/w8x-to-uwp-root).

Windows 8.1 projeleri Windows 10 yeniden hedeflemeniz tercih ederseniz, bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Uzantı SDK başvuruları

Visual Basic, C#, C++ ve JavaScript Evrensel Windows Platformu (UWP) uygulamaları, bu uzantı sdk 'ları Windows 10 kullanım dışı bırakılmış apı 'leri kullanmayan sürece Windows 8.1 hedef olan uzantı sdk 'lerine başvurabilir. UWP uygulamaları tarafından başvuranıp başvurulamayacağını öğrenmek için lütfen Uzantı SDK 'Sı satıcı sitesini denetleyin.

Uygulamanız tarafından başvurulan Uzantı SDK 'sının desteklenmediğini belirlerseniz, aşağıdaki adımları gerçekleştirmeniz gerekir:

1. Hataya neden olan projenin adına bakın. Projenizin hedeflediği platform, proje adının yanında parantez içinde belirtilmiştir. örneğin, **myprojectname (Windows 8.1)** , projeniz **myprojectname** 'in platform sürümü Windows 8.1 hedeflediği anlamına gelir.

1. Desteklenmeyen Uzantı SDK 'sına sahip olan satıcının sitesine gidin ve uzantı SDK 'nın sürümünü projenizin hedeflediği platformun sürümü ile uyumlu bağımlılıklarla birlikte yüklemelisiniz.

    > [!NOTE]
    > Bir uzantı SDK 'sının diğer uzantı SDK 'lerinde bağımlılıklara sahip olup olmadığını bulmanın bir yolu, **başvuru Yöneticisi**'ne bakar. Visual Studio yeniden başlatın, yeni bir C# UWP uygulama projesi oluşturun ve ardından projeye sağ tıklayıp **başvuru ekle**' yi seçin. **Windows** sekmesine ve sonra **uzantılar** alt sekmesine gidip uzantı SDK 'sını seçin. **Başvuru Yöneticisi**' nde sağ bölmeye bakın. Bağımlılıklar varsa, burada listelenir.

    > [!IMPORTANT]
    > projeniz Windows 10 hedefliyorsanız ve önceki adımda yüklenen uzantı SDK 'nın Microsoft Visual C++ çalışma zamanı paketine bağımlılığı varsa, Windows 10 ile uyumlu Microsoft Visual C++ çalışma zamanı paketinin sürümü v 14.0 ve Visual Studio ile yüklenir.

1. Önceki adımda yüklediğiniz Uzantı SDK diğer uzantı SDK 'larına bağımlılıklar içeriyorsa, bağımlılıklara sahip olan satıcıların sitelerine gidin ve projenizin hedeflediği platformun sürümü ile uyumlu olan bu bağımlılıkların sürümlerini yükleyebilirsiniz.

1. Visual Studio yeniden başlatın ve uygulamanızı açın.

1. Projede hataya neden olan **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

1. **Windows** sekmesine ve sonra **uzantılar** alt sekmesine tıklayın ve ardından eski uzantı sdk 'larının onay kutularının işaretini kaldırın ve yeni uzantı sdk 'larının onay kutularını işaretleyin. **Tamam**'a tıklayın.

## <a name="add-a-reference-at-design-time"></a>Tasarım zamanında başvuru ekleme

projenizdeki bir derlemeye başvuru yaptığınızda, Visual Studio derlemeyi aşağıdaki konumlarda arar:

- Geçerli proje dizini. (Bu derlemeleri, **tarayıcı** sekmesini kullanarak bulabilirsiniz.)

- Aynı çözümdeki diğer proje dizinleri. (Bu derlemeleri **Projeler** sekmesinde bulabilirsiniz.)

> [!NOTE]
> - Tüm projeler **mscorlib**'e örtük bir başvuru içerir.
> - Tüm projeler `System.Core` , `System.Core` Başvurular listesinden kaldırılsa bile, için örtük bir başvuru içerir.
> - Visual Basic projeler için örtük bir başvuru içerir <xref:Microsoft.VisualBasic> .

## <a name="references-to-shared-components-at-run-time"></a>Çalışma zamanında paylaşılan bileşenlere başvurular

Çalışma zamanında, bileşenlerin ya projenin çıkış yolunda ya da genel derleme önbelleğinde (GAC) olması gerekir. Proje, bu konumlardan birinde olmayan bir nesneye başvuru içeriyorsa, projeyi oluşturduğunuzda projenin çıkış yoluna başvuruyu kopyalamanız gerekir. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>Özelliği, bu kopyanın yapılıp yapılmayacağını belirtir. Değer **true** ise, projeyi oluşturduğunuzda başvuru proje dizinine kopyalanır. Değer **false** ise, başvuru kopyalanmaz.

GAC 'de kayıtlı bir özel bileşene başvuru içeren bir uygulama dağıtırsanız, bu ayar ne olursa olsun bileşen uygulamayla birlikte dağıtılmaz <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> . Visual Studio önceki sürümlerinde, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derlemenin dağıtılmasını sağlamak için bir başvuru üzerinde özelliğini ayarlayabilirsiniz. Şimdi, derlemeyi \bin klasörüne el ile eklemeniz gerekir. Bu, tüm özel kodu scrutlı 'in altına koyar ve alışık olduğunuz özel kodu yayımlama riskini azaltır.

Varsayılan olarak, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derleme veya bileşen genel derleme önbelleğiyle veya bir çerçeve bileşeni ise, özelliği **false** olarak ayarlanır. Aksi takdirde, değer **true** olarak ayarlanır. Project-proje başvuruları her zaman **True** olarak ayarlanır.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>.NET 'in farklı bir sürümünü hedefleyen bir proje veya derlemeye başvuru

.NET 'in farklı bir sürümünü hedefleyen projelere veya derlemelere başvuran uygulamalar oluşturabilirsiniz. örneğin, .NET Framework 4,5 ' i hedefleyen bir derlemeye başvuran .NET Framework 4,6 ' i hedefleyen bir uygulama oluşturabilirsiniz. .NET 'in önceki bir sürümünü hedefleyen bir proje oluşturursanız, bu projedeki bir başvuruyu, daha yeni bir sürümü hedefleyen bir projeye veya derlemeye ayarlayamazsınız.

Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Project-proje başvuruları

Project proje başvuruları, derlemeler içeren projelere referanslardır; proje başvurularını başvuru Yöneticisi iletişim kutusunun **Projeler** sekmesini kullanarak eklersiniz. Visual Studio, projenin yolunu verildiğinde bir derlemeyi bulabilir.

Derleme üreten bir projeniz varsa, projeye başvurmanız ve dosya başvurusu kullanmamalısınız (aşağıya bakın). Proje-proje başvurusunun avantajı, derleme sistemindeki projeler arasında bir bağımlılık oluşturmasıdır. Bağımlı proje, başvuran projenin en son derlenmesinden bu yana değiştirilmişse oluşturulur. Bir dosya başvurusu, derleme bağımlılığı oluşturmaz, bu nedenle, bağımlı proje oluşturmadan başvuran projeyi derlemek mümkündür ve başvuru kullanımdan kalkabilir. (Yani, proje projenin daha önce oluşturulmuş bir sürümüne başvurabilir.) Bu, *bin* dizininde tek bir dll 'nin gerekli olmasının oluşmasına neden olabilir ve bu mümkün değildir. Bu çakışma oluştuğunda "Uyarı: proje ' proje ' içindeki ' dosya ' bağımlılığı ' dosyası, ' File. '" başvurusunun üzerine yazabileceğinden çalıştırma dizinine kopyalanamıyor gibi bir ileti görürsünüz. Daha fazla bilgi için bkz. [bozuk başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md) ve [nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> bir projenin .NET Framework hedef sürümü 4,5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3,5 veya 4,0 ise, projeden projeye başvuru yerine bir dosya başvurusu oluşturulur.

## <a name="shared-project-references"></a>Paylaşılan proje başvuruları

Diğer çoğu proje türünden farklı olarak, *paylaşılan bir proje* herhangi bir ikili çıkış içermez. Bunun yerine, kod kendisine başvuran her bir proje için derlenir. [Paylaşılan projeler](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) , bir dizi farklı uygulama projesinin başvurduğu ortak kod yazmanızı sağlar. Kod, başvuran her projenin bir parçası olarak derlenir ve platforma özgü işlevlerin paylaşılan kod tabanına dahil olması için derleyici yönergeleri içerebilir. Başvuru Yöneticisi iletişim kutusunun **Paylaşılan projeler** sekmesinde paylaşılan bir projeye bir başvuru ekleyin.

## <a name="file-references"></a>Dosya başvuruları

dosya başvuruları, bir Visual Studio projesi bağlamı dışındaki derlemelere doğrudan referanslardır. Bunları, başvuru Yöneticisi iletişim kutusunun **tarayıcı** sekmesini kullanarak oluşturabilirsiniz. Yalnızca bir derleme veya bileşen varsa ve bunu çıkış olarak oluşturan projeyi değil, bir dosya başvurusu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bozuk başvurularda sorun giderme](../ide/troubleshooting-broken-references.md)
- [Nasıl yapılır: başvuruları ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
