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
ms.openlocfilehash: 9623e8ffb6a315851d26cd06defb62899e429f44
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591261"
---
# <a name="manage-references-in-a-project"></a>Bir projedeki başvuruları yönetme

Harici bir bileşene veya bağlı bir hizmete karşı kod yazmadan önce, projenizin önce buna bir başvuru içermesi gerekir. Başvuru, temelde Visual Studio'nun bileşeni veya hizmeti bulmak için ihtiyaç duyduğu bilgileri içeren bir proje dosyasındaki giriştir.

Başvuru eklemek **için, Çözüm Gezgini'ndeki** **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle'yi**seçin. Ayrıca proje düğümüne sağ tıklayıp**Referans** **Ekle'yi** > seçebilirsiniz. Daha fazla bilgi için [bkz: Başvuru ekleme veya kaldırma.](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)

![Visual C&#43;&#43;'da referans ekleme](../ide/media/vs2015_cpp_add_reference.png)

Aşağıdaki bileşen ve hizmet türlerine bir başvuru ekleyebilirsiniz:

- .NET sınıf kitaplıkları veya derlemeleri

- UWP uygulamaları

- COM bileşenleri

- Aynı çözümdeki projelerin diğer derlemeleri veya sınıf kitaplıkları

- Paylaşılan projeler

- XML Web hizmetleri

## <a name="uwp-app-references"></a>UWP uygulama referansları

### <a name="project-references"></a>Proje başvuruları

Evrensel Windows Platformu (UWP) projeleri, bu projelerin Windows 10'da amortismana alınmış API'leri kullanmaması koşuluyla, çözümdeki diğer UWP projelerine veya Windows 8.1 projelerine veya ikililerine başvurular oluşturabilir. Daha fazla bilgi için bkz: [Windows Runtime 8'den UWP'ye taşı.](/windows/uwp/porting/w8x-to-uwp-root)

Windows 8.1 projelerini Windows 10'a yeniden hedeflemeyi seçerseniz, [Bkz. Bağlantı Noktası, geçiş ve Visual Studio projelerini yükseltin.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

### <a name="extension-sdk-references"></a>Uzatma SDK referansları

Visual Basic, C#, C++ ve JavaScript Evrensel Windows Platformu (UWP) uygulamaları, bu Uzantı Lı SDK'lar Windows 10'da amortismana alınmış API'leri kullanmadığı sürece Windows 8.1'i hedefleyen Uzantı SDK'larına başvurur. UWP uygulamaları tarafından başvurulup başvurulamayacağını öğrenmek için lütfen Uzantı SDK satıcı sitesini kontrol edin.

Uygulamanız tarafından başvurulan Uzantı SDK'sının desteklenmediğini belirlerseniz, aşağıdaki adımları gerçekleştirmeniz gerekir:

1. Hataya neden olan projenin adına bakın. Projenizin hedef aldığı platform, proje adının yanındaki parantez içinde belirtilir. Örneğin, **MyProjectName (Windows 8.1),** projeniz **MyProjectName'in** windows 8.1 platform sürümünü hedeflemesi anlamına gelir.

1. Desteklenmeyen Uzantı SDK'sının sahibi satıcının sitesine gidin ve Uzantı SDK sürümünü projenizin hedeflediğiniz platformun sürümüyle uyumlu bağımlılıklarla yükleyin.

    > [!NOTE]
    > Bir Uzantı SDK'nın diğer Uzantı SDK'larına bağımlılığı olup olmadığını öğrenmenin bir **yolu, Başvuru Yöneticisi'ne**bakmaktır. Visual Studio'yu yeniden başlatın, yeni bir C# UWP uygulama projesi oluşturun ve ardından projeye sağ tıklayın ve **Referans Ekle'yi**seçin. **Windows** sekmesine, ardından **Uzantılar** alt sekmesine gidin ve Uzantı SDK'sını seçin. **Başvuru Yöneticisi'ndeki**sağ bölmeye bakın. Bağımlılıkları varsa, orada listelenir.

    > [!IMPORTANT]
    > Projeniz Windows 10'u hedefliyorsa ve önceki adımda yüklü olan Uzantı SDK'sının Microsoft Visual C++ Çalışma Zamanı Paketi'ne bağımlılığı varsa, Windows 10 ile uyumlu Microsoft Visual C++ Çalışma Zamanı Paketi sürümü v14.0'dır ve yüklenir Visual Studio ile birlikte.

1. Önceki adımda yüklediğiniz Uzantı SDK'sının diğer Uzantı SDK'larına bağımlılığı varsa, bağımlılıkların sahibi satıcıların sitelerine gidin ve projenizin platformun sürümüyle uyumlu olan bu bağımlılıkların sürümlerini yükleyin Hedefleme.

1. Visual Studio'yı yeniden başlatın ve uygulamanızı açın.

1. Hataya neden olan projedeki **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Kaynak Ekle'yi**seçin.

1. **Windows** sekmesini ve ardından **Uzantılar** alt sekmesini tıklatın, ardından eski Uzantı SDK'larının onay kutularını kaldırın ve yeni Uzantı SDK'larının onay kutularını işaretleyin. **Tamam**'a tıklayın.

## <a name="add-a-reference-at-design-time"></a>Tasarım zamanında referans ekleme

Projenizdeki bir derlemeye başvuru yaptığınızda, Visual Studio derlemeyi aşağıdaki konumlarda arar:

- Geçerli proje dizini. **(Gözat** sekmesini kullanarak bu derlemeleri bulabilirsiniz.)

- Aynı çözümdeki diğer proje dizinleri. (Bu derlemeleri **Projeler** sekmesinde bulabilirsiniz.)

> [!NOTE]
> - Tüm projeler **mscorlib**için zımni bir referans içerir.
> - Tüm `System.Core`projeler, başvuru listesinden `System.Core` kaldırılsa bile zımni bir başvuru içerir.
> - Visual Basic projeleri için <xref:Microsoft.VisualBasic>zımni bir başvuru içerir.

## <a name="references-to-shared-components-at-run-time"></a>Çalışma zamanında paylaşılan bileşenlere başvurular

Çalışma zamanında bileşenler, projenin çıktı yolunda veya Genel Montaj Önbelleğinde (GAC) olmalıdır. Proje, bu konumlardan birinde olmayan bir nesneye başvuruda bulunmuyorsa, projeyi oluştururken başvuruyu projenin çıktı yoluna kopyalamanız gerekir. Özellik, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> bu kopyanın yapılması gerekip gerekmediğini gösterir. Değer **True**ise, projeyi oluştururken başvuru proje dizinine kopyalanır. Değer **False**ise, başvuru kopyalanmaz.

GAC'de kayıtlı özel bir bileşene başvuru içeren bir uygulama dağıtırsanız, bileşen <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> ayarı ne olursa olsun uygulamayla birlikte dağıtılacak. Visual Studio'nun önceki sürümlerinde, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derlemenin dağıtıldığından emin olmak için özelliği bir başvuruüzerine ayarlayabilirsiniz. Şimdi, derlemeyi \Bin klasörüne el ile eklemeniz gerekir. Bu, tüm özel kodları inceleme altına alar ve aşina olmadığınız özel kod yayımlama riskini azaltır.

Varsayılan olarak, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derleme veya bileşen genel montaj önbelleğindeyse veya bir çerçeve bileşeniyse, özellik **False** olarak ayarlanır. Aksi takdirde, değer **True**olarak ayarlanır. Projeden projeye başvurular her zaman **True**olarak ayarlanır.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>.NET'in farklı bir sürümünü hedefleyen bir proje veya derlemeye başvurun

.NET'in farklı bir sürümünü hedefleyen projelere veya derlemelere başvuran uygulamalar oluşturabilirsiniz. Örneğin, .NET Framework 4.6'yı hedefleyen ve .NET Framework 4.5'i hedefleyen bir derlemeye başvuran bir uygulama oluşturabilirsiniz. .NET'in önceki bir sürümünü hedefleyen bir proje oluşturursanız, bu projedeki bir başvuruyuz, daha yeni bir sürümü hedefleyen bir proje veya derlemeye ayarlayamazsınız.

Daha fazla bilgi için çerçeve [hedefleme genel bakış'a](../ide/visual-studio-multi-targeting-overview.md)bakın.

## <a name="project-to-project-references"></a>Projeden projeye referanslar

Projeden projeye başvurular derlemeler içeren projelere yapılan başvurulardır; Başvuru Yöneticisi iletişim kutusunun **Projeler** sekmesini kullanarak proje başvuruları eklersiniz. Visual Studio, projeye giden yol verildiğinde bir derleme bulabilir.

Derleme oluşturan bir projeniz varsa, projeye başvurmalı ve dosya başvurusu kullanmamalısınız (aşağıya bakın). Projeden projeye başvurunun avantajı, yapı sistemindeki projeler arasında bir bağımlılık oluşturmasıdır. Bağımlı proje, başvuru projesinin son inşa edildiği tarihten bu yana değişmişse oluşturulur. Dosya başvurusu bir yapı bağımlılığı oluşturmaz, bu nedenle bağımlı proje oluşturmadan başvuru projesi oluşturmak mümkündür ve başvuru geçersiz hale gelebilir. (Diğer bir şekilde, proje projenin önceden oluşturulmuş bir sürümüne başvurulabilir.) Bu, tek bir DLL'nin depo *gözü* dizininde gerekli olan birkaç sürümüne neden olabilir, bu mümkün değildir. Bu çakışma oluştuğunda, "Uyarı: proje 'proje'deki bağımlılık 'dosyası' başvuru 'dosyası'nın üzerine yazacağı için çalıştırılamayan dizine kopyalanamaz. Daha fazla bilgi için, [bozuk başvuruları giderme sorununa](../ide/troubleshooting-broken-references.md) bakın ve [nasıl yapılır: Proje bağımlılıklarını oluşturun ve kaldırın.](../ide/how-to-create-and-remove-project-dependencies.md)

> [!NOTE]
> Bir projenin .NET Framework'ünün hedef sürümü sürüm 4.5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3.5 veya 4.0 ise proje-proje başvurusu yerine bir dosya başvurusu oluşturulur.

## <a name="shared-project-references"></a>Paylaşılan proje başvuruları

Diğer proje türlerinin aksine, paylaşılan bir *projenin* ikili çıktısı yoktur. Bunun yerine, kod, başvurulan her projede derlenir. [Paylaşılan Projeler,](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) bir dizi farklı uygulama projesitarafından başvurulan ortak kodu yazmanıza izin sağlar. Kod, her başvuru projesinin bir parçası olarak derlenir ve platforma özgü işlevselliği paylaşılan kod tabanına eklemeye yardımcı olmak için derleyici yönergeleri içerebilir. Başvuru Yöneticisi iletişim kutusunun **Paylaşılan Projeler** sekmesinde paylaşılan bir projeye başvuru ekleyin.

## <a name="file-references"></a>Dosya başvuruları

Dosya başvuruları, Visual Studio projesinin bağlamı dışındaki derlemelere doğrudan başvurur. Bunları, Başvuru Yöneticisi iletişim kutusunun **Gözat** sekmesini kullanarak oluşturursunuz. Bir dosya başvurucuzun bir derlemeveya bileşeniniz olduğunda kullanın, çıktı olarak oluşturan projeyi değil.

## <a name="see-also"></a>Ayrıca bkz.

- [Bozuk başvurularda sorun giderme](../ide/troubleshooting-broken-references.md)
- [Nasıl yapılı: Başvuru ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
