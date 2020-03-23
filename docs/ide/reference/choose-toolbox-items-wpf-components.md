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
ms.openlocfilehash: 731fe05e90e01c60f0a7ff3a14917d6d7625bc1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570563"
---
# <a name="choose-toolbox-items-wpf-components"></a>Araç Kutusu öğelerini, WPF bileşenlerini seçme

Araç Kutusu **Öğeleriseç** iletişim kutusunun bu sekmesi, yerel bilgisayarınızda bulunan Windows Sunu Temeli (WPF) denetimlerinin listesini görüntüler. Bu listeyi görüntülemek için **Araçlar** menüsünden **Araç Kutusu Öğelerini Seç** iletişim kutusunu görüntülemek için Araç Kutusu **Öğelerini Seçin'i** seçin ve ardından **WPF Bileşenleri** sekmesini seçin. Listelenen bileşenleri sıralamak için herhangi bir sütun başlığı seçin.

- Bir bileşenin yanındaki onay kutusu seçildiğinde, bu bileşen için bir simge **Araç Kutusu'nda**görüntülenir.

    > [!TIP]
    > Düzenleme için açık olan bir proje belgesine WPF denetimi eklemek **için, Araç Kutusu** simgesini Tasarım görünüm yüzeyine sürükleyin. Bileşenin varsayılan biçimlendirmesi ve kodu projenize eklenir ve değiştirmenize hazırdır. Daha fazla bilgi için [Toolbox'a](../../ide/reference/toolbox.md)bakın.

- Bir bileşenin yanındaki onay kutusu temizlendiğinde, ilgili simge **Araç Kutusu'ndan**kaldırılır.

    > [!NOTE]
    > Bilgisayarınıza yüklenen .NET bileşenleri, araç simgeleraraç **kutusunda**görüntülenip görüntülenmemesi durumunda kullanılabilir durumda kalır.

**WPF Bileşenleri** sekmesindeki sütunlar aşağıdaki bilgileri içerir:

**Adı**

Bilgisayarınızın kayıt defterinde girişlerin bulunduğu WPF denetimlerinin adlarını listeler.

**Namespace**

Bileşenin yapısını tanımlayan [.NET API](/dotnet/api/?view=netframework-4.7) ad alanının hiyerarşisini görüntüler. Bilgisayarınızda yüklü her .NET ad alanı içindeki kullanılabilir bileşenleri listelemek için bu sütunda sıralayın.

**Montaj Adı**

Her bileşen için ad alanını içeren .NET derlemesinin adını görüntüler. Bilgisayarınızda yüklü her .NET derlemesinde bulunan ad alanlarını listelemek için bu sütunda sıralayın.

**Dizin**

.NET derlemesinin konumunu görüntüler. Tüm derlemeler için varsayılan konum, Genel Montaj Önbelleği'dir. Genel Montaj Önbelleği hakkında daha fazla bilgi için [derlemelerle çalışma ve Genel Montaj Önbelleği'ne](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac)bakın.

## <a name="uielement-list"></a>UIElement Listesi

### <a name="filter"></a>Filtre

Metin kutusunda sağladığınız dizeyi temel alan WPF denetimleri listesini filtreler. Dört sütunun herhangi birinden tüm eşleşmeler gösterilir.

**Temizle**

Filtre dizesini temizler.

**Gözat**

WPF denetimleri içeren derlemelere gezinmenizi sağlayan **Açık** iletişim kutusunu açar. Bunu, Genel Montaj Önbelleğinde bulunmayan derlemeleri yüklemek için kullanın.

**Dil**

Seçili WPF denetimini içeren derlemenin yerelleştirilmiş dilini gösterir.

## <a name="limitations"></a>Sınırlamalar

Özel denetim veya <xref:System.Windows.Controls.UserControl> Araç Kutusu'na eklemenin aşağıdaki sınırlamaları vardır:

- Yalnızca geçerli proje dışında tanımlanan özel denetimler için çalışır.

- Çözüm yapılandırmasını Hata Ayıklama'dan Sürüm'e veya Release'den Hata Ayıklama'ya değiştirdiğinizde doğru şekilde güncelleştirilmez. Bunun nedeni, başvurunun bir proje başvurusu olmaması, bunun yerine diskteki derleme için olmasıdır. Denetim geçerli çözümün bir parçasıysa, Hata Ayıklama'dan Sürüm'e değiştirdiğinizde, projeniz denetimin Hata Ayıklama sürümüne başvurmaya devam eder.

Buna ek olarak, tasarım zamanı meta verileri özel denetime uygulanırsa ve bu meta veriler [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) olarak ayarlanmış olduğunu `false`belirtirse, denetim Araç Kutusu'nda görünmez.

Denetiminiz için ad alanı ve derleme eşleme yaparak denetimlerinizi doğrudan XAML görünümünde başvurulayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
- [WPF kullanmaya başlama](../../designers/getting-started-with-wpf.md)
