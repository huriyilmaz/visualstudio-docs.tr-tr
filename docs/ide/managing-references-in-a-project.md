---
title: Bir projedeki başvuruları yönetme
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55b0d3487eb18db33805b418882f157d55b1253
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183541"
---
# <a name="manage-references-in-a-project"></a>Bir projedeki başvuruları yönetme

Bir dış bileşene veya bağlı hizmete karşı kod yazmadan önce, projenizin bir başvurusu içermesi gerekir. Başvuru temelde, Visual Studio 'Nun bileşeni veya hizmeti bulması için gereken bilgileri içeren bir proje dosyasındaki giriştir.

Başvuru eklemek için, **Çözüm Gezgini** ' deki **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. Ayrıca, proje düğümüne sağ tıklayıp başvuru **Ekle**' yi seçebilirsiniz  >  **Reference**. Daha fazla bilgi için bkz. [nasıl yapılır: başvuruları ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

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

Evrensel Windows Platformu (UWP) projeleri, bu projelerin Windows 10 ' da kullanım dışı bırakılan API 'Leri kullanmadığından, çözümdeki diğer UWP projelerine veya Windows 8.1 projelere veya ikili dosyalara başvurular oluşturabilir. Daha fazla bilgi için, bkz. [Windows çalışma zamanı 8 ' den UWP 'e taşıma](/windows/uwp/porting/w8x-to-uwp-root).

Windows 8.1 projelerini Windows 10 ' a yeniden hedeflemeniz tercih ederseniz bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Uzantı SDK başvuruları

Visual Basic, C#, C++ ve JavaScript Evrensel Windows Platformu (UWP) uygulamaları, bu uzantı SDK 'ları Windows 10 ' da kullanım dışı bırakılan API 'Leri kullanmadığından Windows 8.1 hedef olan Uzantı SDK 'Lerine başvurabilir. UWP uygulamaları tarafından başvuranıp başvurulamayacağını öğrenmek için lütfen Uzantı SDK 'Sı satıcı sitesini denetleyin.

Uygulamanız tarafından başvurulan Uzantı SDK 'sının desteklenmediğini belirlerseniz, aşağıdaki adımları gerçekleştirmeniz gerekir:

1. Hataya neden olan projenin adına bakın. Projenizin hedeflediği platform, proje adının yanında parantez içinde belirtilmiştir. Örneğin, **MyProjectName (Windows 8.1)** , projeniz **MyProjectName** 'in platform sürümü Windows 8.1 hedeflediği anlamına gelir.

1. Desteklenmeyen Uzantı SDK 'sına sahip olan satıcının sitesine gidin ve uzantı SDK 'nın sürümünü projenizin hedeflediği platformun sürümü ile uyumlu bağımlılıklarla birlikte yüklemelisiniz.

    > [!NOTE]
    > Bir uzantı SDK 'sının diğer uzantı SDK 'lerinde bağımlılıklara sahip olup olmadığını bulmanın bir yolu, **başvuru Yöneticisi**'ne bakar. Visual Studio 'Yu yeniden başlatın, yeni bir C# UWP uygulaması projesi oluşturun ve ardından projeye sağ tıklayıp **Başvuru Ekle**' yi seçin. **Windows** sekmesine, ardından **Uzantılar** alt sekmesine gidip Uzantı SDK 'sını seçin. **Başvuru Yöneticisi**' nde sağ bölmeye bakın. Bağımlılıklar varsa, burada listelenir.

    > [!IMPORTANT]
    > Projeniz Windows 10 ' u hedefliyorsanız ve önceki adımda yüklenen Uzantı SDK 'nın Microsoft Visual C++ çalışma zamanı paketine bağımlılığı varsa, Windows 10 ile uyumlu olan Microsoft Visual C++ çalışma zamanı paketinin sürümü v 14.0 ve Visual Studio ile birlikte yüklenir.

1. Önceki adımda yüklediğiniz Uzantı SDK diğer uzantı SDK 'larına bağımlılıklar içeriyorsa, bağımlılıklara sahip olan satıcıların sitelerine gidin ve projenizin hedeflediği platformun sürümü ile uyumlu olan bu bağımlılıkların sürümlerini yükleyebilirsiniz.

1. Visual Studio 'Yu yeniden başlatın ve uygulamanızı açın.

1. Projede hataya neden olan **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

1. **Windows** sekmesine ve sonra **Uzantılar** alt sekmesine tıklayın ve ardından eski Uzantı SDK 'larının onay kutularının Işaretini kaldırın ve yeni uzantı SDK 'larının onay kutularını işaretleyin. **Tamam**'a tıklayın.

## <a name="add-a-reference-at-design-time"></a>Tasarım zamanında başvuru ekleme

Projenizdeki bir derlemeye başvuru yaptığınızda, Visual Studio derlemeyi aşağıdaki konumlarda arar:

- Geçerli proje dizini. (Bu derlemeleri, **tarayıcı** sekmesini kullanarak bulabilirsiniz.)

- Aynı çözümdeki diğer proje dizinleri. (Bu derlemeleri **Projeler** sekmesinde bulabilirsiniz.)

> [!NOTE]
> - Tüm projeler **mscorlib**'e örtük bir başvuru içerir.
> - Tüm projeler `System.Core` , `System.Core` Başvurular listesinden kaldırılsa bile, için örtük bir başvuru içerir.
> - Visual Basic projeler için örtük bir başvuru içerir <xref:Microsoft.VisualBasic> .

## <a name="references-to-shared-components-at-run-time"></a>Çalışma zamanında paylaşılan bileşenlere başvurular

Çalışma zamanında, bileşenlerin ya projenin çıkış yolunda ya da genel derleme önbelleğinde (GAC) olması gerekir. Proje, bu konumlardan birinde olmayan bir nesneye başvuru içeriyorsa, projeyi oluşturduğunuzda projenin çıkış yoluna başvuruyu kopyalamanız gerekir. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>Özelliği, bu kopyanın yapılıp yapılmayacağını belirtir. Değer **true**ise, projeyi oluşturduğunuzda başvuru proje dizinine kopyalanır. Değer **false**ise, başvuru kopyalanmaz.

GAC 'de kayıtlı bir özel bileşene başvuru içeren bir uygulama dağıtırsanız, bu ayar ne olursa olsun bileşen uygulamayla birlikte dağıtılmaz <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> . Visual Studio 'nun önceki sürümlerinde, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derlemenin dağıtılmasını sağlamak için bir başvuru üzerinde özelliğini ayarlayabilirsiniz. Şimdi, derlemeyi \bin klasörüne el ile eklemeniz gerekir. Bu, tüm özel kodu scrutlı 'in altına koyar ve alışık olduğunuz özel kodu yayımlama riskini azaltır.

Varsayılan olarak, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derleme veya bileşen genel derleme önbelleğiyle veya bir çerçeve bileşeni ise, özelliği **false** olarak ayarlanır. Aksi takdirde, değer **true**olarak ayarlanır. Projeden projeye başvurular her zaman **true**olarak ayarlanır.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>.NET 'in farklı bir sürümünü hedefleyen bir proje veya derlemeye başvuru

.NET 'in farklı bir sürümünü hedefleyen projelere veya derlemelere başvuran uygulamalar oluşturabilirsiniz. Örneğin, .NET Framework 4,5 ' i hedefleyen bir derlemeye başvuran .NET Framework 4,6 ' i hedefleyen bir uygulama oluşturabilirsiniz. .NET 'in önceki bir sürümünü hedefleyen bir proje oluşturursanız, bu projedeki bir başvuruyu, daha yeni bir sürümü hedefleyen bir projeye veya derlemeye ayarlayamazsınız.

Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Projeden projeye başvurular

Projeden projeye başvurular, derlemeler içeren projelere referanslardır; proje başvurularını başvuru Yöneticisi iletişim kutusunun **Projeler** sekmesini kullanarak eklersiniz. Visual Studio, projenin yolunu verildiğinde bir derlemeyi bulabilir.

Derleme üreten bir projeniz varsa, projeye başvurmanız ve dosya başvurusu kullanmamalısınız (aşağıya bakın). Proje-proje başvurusunun avantajı, derleme sistemindeki projeler arasında bir bağımlılık oluşturmasıdır. Bağımlı proje, başvuran projenin en son derlenmesinden bu yana değiştirilmişse oluşturulur. Bir dosya başvurusu, derleme bağımlılığı oluşturmaz, bu nedenle, bağımlı proje oluşturmadan başvuran projeyi derlemek mümkündür ve başvuru kullanımdan kalkabilir. (Yani, proje projenin daha önce oluşturulmuş bir sürümüne başvurabilir.) Bu, *bin* dizininde tek bir dll 'nin gerekli olmasının oluşmasına neden olabilir ve bu mümkün değildir. Bu çakışma oluştuğunda "Uyarı: proje ' proje ' içindeki ' dosya ' bağımlılığı ' dosyası, ' File. '" başvurusunun üzerine yazabileceğinden çalıştırma dizinine kopyalanamıyor gibi bir ileti görürsünüz. Daha fazla bilgi için bkz. [bozuk başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md) ve [nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Bir projenin .NET Framework hedef sürümü 4,5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3,5 veya 4,0 ise, projeden projeye başvuru yerine bir dosya başvurusu oluşturulur.

## <a name="shared-project-references"></a>Paylaşılan proje başvuruları

Diğer çoğu proje türünden farklı olarak, *paylaşılan bir proje* herhangi bir ikili çıkış içermez. Bunun yerine, kod kendisine başvuran her bir proje için derlenir. [Paylaşılan projeler](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) , bir dizi farklı uygulama projesinin başvurduğu ortak kod yazmanızı sağlar. Kod, başvuran her projenin bir parçası olarak derlenir ve platforma özgü işlevlerin paylaşılan kod tabanına dahil olması için derleyici yönergeleri içerebilir. Başvuru Yöneticisi iletişim kutusunun **Paylaşılan projeler** sekmesinde paylaşılan bir projeye bir başvuru ekleyin.

## <a name="file-references"></a>Dosya başvuruları

Dosya başvuruları, Visual Studio projesi bağlamı dışındaki derlemelere doğrudan referanslardır. Bunları, başvuru Yöneticisi iletişim kutusunun **tarayıcı** sekmesini kullanarak oluşturabilirsiniz. Yalnızca bir derleme veya bileşen varsa ve bunu çıkış olarak oluşturan projeyi değil, bir dosya başvurusu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bozuk başvurularda sorun giderme](../ide/troubleshooting-broken-references.md)
- [Nasıl yapılır: başvuruları ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
