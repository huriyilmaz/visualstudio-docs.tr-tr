---
title: Araç Kutusu Öğelerini, WPF Bileşenlerini Seçme
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28576fab1ed4b39810b6f4cc32fb2955a7a44039
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099355"
---
# <a name="choose-toolbox-items-wpf-components"></a>Araç Kutusu öğelerini, WPF bileşenlerini seçme

**Araç kutusu öğelerini Seç** iletişim kutusunun bu sekmesi, yerel bilgisayarınızda bulunan WINDOWS PRESENTATION FOUNDATION (WPF) denetimlerinin bir listesini görüntüler. Bu listeyi göstermek için **Araçlar** menüsünden **araç kutusu** öğelerini Seç ' i seçerek **araç kutusu öğelerini Seç** Iletişim kutusunu görüntüleyin ve ardından **WPF bileşenleri** sekmesini seçin. Listelenen bileşenleri sıralamak için herhangi bir sütun başlığını seçin.

- Bir bileşenin yanındaki onay kutusu seçildiğinde, bu bileşen için bir simge **araç kutusunda**görüntülenir.

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

**Dizinden**

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

Ayrıca, tasarım zamanı meta verileri özel denetime uygulanırsa ve bu meta veriler [Microsoft. Windows. Design. ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) ' ın olarak ayarlandığını belirtir `false` , Denetim araç kutusunda görünmez.

Denetimlerinizin ad alanını ve derlemesini eşleyerek doğrudan XAML görünümünde denetimlerine başvurabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
- [WPF kullanmaya başlama](../../designers/getting-started-with-wpf.md)
