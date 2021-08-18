---
title: Araç Kutusu Öğelerini, WPF Bileşenlerini Seçme
description: yerel bilgisayarınızda seçilebilir Windows Presentation Foundation denetimleri göstermek için WPF bileşenleri sekmesini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9ca6d95de8aec31042309d2b06e3b3b4b1ce5ff2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151762"
---
# <a name="choose-toolbox-items-wpf-components"></a>Araç Kutusu öğelerini, WPF bileşenlerini seçme

**araç kutusu öğelerini seç** iletişim kutusunun bu sekmesi, yerel bilgisayarınızda bulunan Windows Presentation Foundation (WPF) denetimlerinin bir listesini görüntüler. Bu listeyi göstermek için **Araçlar** menüsünden **araç kutusu** öğelerini Seç ' i seçerek **araç kutusu öğelerini Seç** Iletişim kutusunu görüntüleyin ve ardından **WPF bileşenleri** sekmesini seçin. Listelenen bileşenleri sıralamak için herhangi bir sütun başlığını seçin.

- Bir bileşenin yanındaki onay kutusu seçildiğinde, bu bileşen için bir simge **araç kutusunda** görüntülenir.

    > [!TIP]
    > Düzenlenmek üzere açılmış bir proje belgesine WPF denetimi eklemek için, **araç kutusu** simgesini Tasarım görünümü yüzeyine sürükleyin. Bileşen için varsayılan biçimlendirme ve kod, değiştirmeniz için hazır olan projenize eklenir. Daha fazla bilgi için bkz. [araç kutusu](../../ide/reference/toolbox.md).

- Bir bileşenin yanındaki onay kutusu silinirse, ilgili simge **araç kutusu**'ndan kaldırılır.

    > [!NOTE]
    > Bilgisayarınızda yüklü olan .NET bileşenleri, **araç kutusu**'nda görüntülenen simgelerin görüntülenip görüntülenmeksizin kullanılabilir durumda kalır.

**WPF bileşenleri** sekmesindeki sütunlar aşağıdaki bilgileri içerir:

**Ad**

Bilgisayarınızın kayıt defterinde bulunan girdilerin bulunduğu WPF denetimlerinin adlarını listeler.

**Ad Alanı**

Bileşenin yapısını tanımlayan [.NET API](/dotnet/api/?view=netframework-4.7&preserve-view=true) ad alanı hiyerarşisini görüntüler. Bilgisayarınızda yüklü olan her bir .NET ad alanı içindeki kullanılabilir bileşenleri listelemek için bu sütunda sıralama yapın.

**Bütünleştirilmiş kod adı**

Her bileşen için ad alanını içeren .NET derlemesinin adını görüntüler. Bilgisayarınızda yüklü olan her bir .NET derlemesinde bulunan ad alanlarını listelemek için bu sütunda sıralama yapın.

**Dizin**

.NET derlemesinin konumunu görüntüler. Tüm derlemeler için varsayılan konum genel derleme önbelleğidir. Genel derleme önbelleği hakkında daha fazla bilgi için bkz. [derlemeler ve genel derleme önbelleği Ile çalışma](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>UIElement Listesi

### <a name="filter"></a>Filtre

Metin kutusunda sağladığınız dizeye göre WPF denetimleri listesini filtreler. Dört sütundan oluşan tüm eşleşmeler gösterilir.

**Temizle**

Filtre dizesini temizler.

**Gözat**

WPF denetimleri içeren derlemelere gitmenizi sağlayan **Aç** iletişim kutusunu açar. Genel derleme önbelleğinde bulunmayan derlemeleri yüklemek için bunu kullanın.

**Dil**

Seçili WPF denetimini içeren derlemenin yerelleştirilmiş dilini gösterir.

## <a name="limitations"></a>Sınırlamalar

Özel bir denetim veya <xref:System.Windows.Controls.UserControl> araç kutusu eklemek aşağıdaki sınırlamalara sahiptir:

- Yalnızca geçerli proje dışında tanımlanan özel denetimler için geçerlidir.

- Çözüm yapılandırmasını hata ayıklamadan Yayınla veya yayından hata ayıklama olarak değiştirdiğinizde doğru şekilde güncelleştirmez. Bunun nedeni, başvurunun bir proje başvurusu olmaması, ancak bunun yerine diskteki derleme içindir. Denetim, geçerli çözümün parçasıysa, hata ayıklamadan yayın olarak değiştirdiğinizde, projeniz denetimin hata ayıklama sürümüne başvurmaya devam eder.

Ayrıca, tasarım zamanı meta verileri özel denetime uygulanırsa ve bu meta veriler [Microsoft. Windows belirtir. Design. ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) , olarak ayarlanır `false` , Denetim araç kutusunda görünmez.

Denetimlerinizin ad alanını ve derlemesini eşleyerek doğrudan XAML görünümünde denetimlerine başvurabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
- [WPF kullanmaya başlama](../../designers/getting-started-with-wpf.md)
