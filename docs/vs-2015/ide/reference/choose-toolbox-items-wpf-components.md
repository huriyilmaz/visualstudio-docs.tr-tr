---
title: Araç kutusu öğelerini, WPF bileşenlerini seçin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c7967635d8e5d64907587fcd1a9b4d84a31d569
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660925"
---
# <a name="choose-toolbox-items-wpf-components"></a>Araç Kutusu Öğelerini, WPF Bileşenlerini Seçme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Araç kutusu öğelerini Seç** iletişim kutusunun bu sekmesi, yerel bilgisayarınızda bulunan WINDOWS PRESENTATION FOUNDATION (WPF) denetimlerinin bir listesini görüntüler. Bu listeyi göstermek için **Araçlar** menüsünden **araç kutusu** öğelerini Seç ' i seçerek **araç kutusu öğelerini Seç** Iletişim kutusunu görüntüleyin ve ardından **WPF bileşenleri** sekmesini seçin. Listelenen bileşenleri sıralamak için herhangi bir sütun başlığını seçin.

- Bir bileşenin yanındaki onay kutusu seçildiğinde, bu bileşen için bir simge **araç kutusunda**görüntülenir.

  > [!TIP]
  > Bir WPF denetiminin bir örneğini, düzenlenmek üzere açık bir proje belgesine eklemek için, **araç kutusu** simgesini Tasarım görünümü yüzeyi üzerine sürükleyin. Bileşen için varsayılan biçimlendirme ve kod, değiştirmeniz için hazır olan projenize eklenir. Daha fazla bilgi için bkz. [nasıl yapılır: araç kutusu penceresini yönetme](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) ve [nasıl yapılır: araç kutusu sekmelerini işleme](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

- Bir bileşenin yanındaki onay kutusu silinirse, ilgili simge **araç kutusundan kaldırılır.**

  > [!NOTE]
  > Bilgisayarınızda yüklü .NET Framework bileşenleri, **araç kutusu**'nda görüntülenip görüntülenmediğini veya bunlara ait simgelerin görüntülenip görüntülenmediğini, kullanılabilir durumda kalır.

  **WPF bileşenleri** sekmesindeki sütunlar aşağıdaki bilgileri içerir:

  Ad, bilgisayarınızın kayıt defterinde bulunan girdilerin bulunduğu WPF denetimlerinin adlarını listeler.

  Ad alanı, bileşenin yapısını tanımlayan [nib: .NET Framework sınıf kitaplığı](https://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) ad alanının hiyerarşisini görüntüler. Bilgisayarınızda yüklü olan her bir .NET Framework ad alanı içindeki kullanılabilir bileşenleri listelemek için bu sütunda sıralama yapın.

  Derleme adı, her bileşen için ad alanını içeren .NET Framework derlemesinin adını görüntüler. Bilgisayarınızda yüklü olan her bir .NET Framework derlemesinde bulunan ad alanlarını listelemek için bu sütunda sıralama yapın.

  Dizin .NET Framework derlemesinin konumunu görüntüler. Tüm derlemeler için varsayılan konum genel derleme önbelleğidir. Genel derleme önbelleği hakkında daha fazla bilgi için bkz. [derlemeler ve genel derleme önbelleği Ile çalışma](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).

## <a name="uielement-list"></a>UIElement Listesi
 **Filtre Uygula** Metin kutusunda sağladığınız dizeye göre WPF denetimleri listesini filtreler. Dört sütundan oluşan tüm eşleşmeler gösterilir.

 **Temizle** Filtre dizesini temizler.

 **Gözatmaya** WPF denetimleri içeren derlemelere gitmenizi sağlayan **Aç** iletişim kutusunu açar. Genel derleme önbelleğinde bulunmayan derlemeleri yüklemek için bunu kullanın.

 **Dil** Seçili WPF denetimini içeren derlemenin yerelleştirilmiş dilini gösterir.

## <a name="limitations"></a>Sınırlamalar
 Araç kutusuna özel denetim veya <xref:System.Windows.Controls.UserControl> eklemek aşağıdaki sınırlamalara sahiptir.

- Yalnızca geçerli proje dışında tanımlanan özel denetimler için geçerlidir.

- Çözüm yapılandırmasını hata ayıklamadan Yayınla veya yayından hata ayıklama olarak değiştirdiğinizde doğru şekilde güncelleştirmez. Bunun nedeni, başvurunun bir proje başvurusu olmaması, ancak bunun yerine diskteki derleme içindir. Denetim, geçerli çözümün parçasıysa, hata ayıklamadan yayın olarak değiştirdiğinizde, projeniz denetimin hata ayıklama sürümüne başvurmaya devam eder.

  Ayrıca, tasarım zamanı meta verileri özel denetime uygulanırsa ve bu meta veriler [ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) `false` olarak ayarlandığını belirtiyorsa, Denetim araç kutusunda görünmez.

  Denetimlerinizin ad alanını ve derlemesini eşleyerek doğrudan XAML görünümünde denetimlerine başvurabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: XAML 'de ad alanı Içeri aktarma](https://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).

## <a name="see-also"></a>Ayrıca bkz.

- [Araç kutusu öğelerini Seç Iletişim kutusu (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Araç Kutusu](../../ide/reference/toolbox.md)
- [Nasıl yapılır: WPF uygulamasında üçüncü taraf WPF denetimi kullanma](https://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)
- [WPF Tasarımcısı](https://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)