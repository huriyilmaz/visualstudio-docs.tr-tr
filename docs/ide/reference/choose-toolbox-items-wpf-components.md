---
title: Araç Kutusu Öğelerini, WPF Bileşenlerini Seçme
description: WpF Bileşenleri sekmesini kullanarak yerel bilgisayarınızda Windows Presentation Foundation denetimlerini görüntülemeyi öğrenin.
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
ms.openlocfilehash: 4d690dddd660227155b36b6b97aff7cc3582d95d397fd5f2fe05ac90b5873724
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412302"
---
# <a name="choose-toolbox-items-wpf-components"></a>Araç Kutusu öğelerini, WPF bileşenlerini seçme

Araç Kutusu Öğelerini **Seç iletişim kutusunun bu** sekmesi, yerel bilgisayarınızda Windows Presentation Foundation (WPF) denetimlerinin listesini görüntüler. Bu listeyi görüntülemek için Araçlar **menüsünden** Araç Kutusu Öğelerini Seç'i seçerek Araç Kutusu Öğelerini Seç iletişim kutusunu **görüntüleyin** ve **ardından WPF Bileşenleri sekmesini** seçin.  Listelenen bileşenleri sıralamak için herhangi bir sütun başlığı seçin.

- Bir bileşenin yanındaki onay kutusu seçildiğinde, Araç Kutusunda bu bileşen için bir **simge görüntülenir.**

    > [!TIP]
    > Düzenleme için açık olan bir proje belgesine WPF denetimi  eklemek için Araç Kutusu simgesini Tasarım görünümü sürükleyin. Bileşenin varsayılan işaretlemesi ve kodu projenize eklenir ve değiştirme için hazır olur. Daha fazla bilgi için [bkz. Araç Kutusu.](../../ide/reference/toolbox.md)

- Bir bileşenin yanındaki onay kutusu temizlenirken ilgili simge Araç Kutusundan **kaldırılır.**

    > [!NOTE]
    > Bilgisayarınızda yüklü olan .NET bileşenleri, araç kutusunda görüntülense de görüntülenmese de **kullanılabilir olmaya devam ediyor.**

WPF Bileşenleri **sekmesindeki sütunlar** aşağıdaki bilgileri içerir:

**Ad**

Bilgisayarınızın kayıt defterinde hangi girdilerin mevcut olduğunu WPF denetimlerinin adlarını listeler.

**Ad Alanı**

Bileşenin yapısını tanımlayan [.NET API](/dotnet/api/?view=netframework-4.7&preserve-view=true) ad alanının hiyerarşisini görüntüler. Bilgisayarınızda yüklü olan her .NET ad alanı içindeki kullanılabilir bileşenleri listeleyene kadar bu sütunda sırala.

**Derleme Adı**

Her bileşen için ad alanını içeren .NET derlemenin adını görüntüler. Bilgisayarınızda yüklü olan her .NET derlemesinde yer alan ad alanlarını listeleyene kadar bu sütunda sırala.

**Dizin**

.NET derlemenin konumunu görüntüler. Tüm derlemeler için varsayılan konum Genel Derleme Önbelleği'dir. Genel Derleme Önbelleği hakkında daha fazla bilgi için [bkz. Derlemelerle çalışma ve Genel Derleme Önbelleği.](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac)

## <a name="uielement-list"></a>UIElement Listesi

### <a name="filter"></a>Filtre

WPF denetimleri listesini, metin kutusunda sağ istediğiniz dizeye göre filtreler. Dört sütundan herhangi bir eşleşme gösterilir.

**Temizle**

Filtre dizesini temizler.

**Gözat**

WPF **denetimleri** içeren derlemelere gitmek için Aç iletişim kutusunu açar. Genel Derleme Önbelleği'nde yer alan derlemeleri yüklemek için bunu kullanın.

**Dil**

Seçilen WPF denetimi içeren derlemenin yerelleştirilmiş dilini gösterir.

## <a name="limitations"></a>Sınırlamalar

Araç Kutusuna veya özel <xref:System.Windows.Controls.UserControl> denetim eklemenin aşağıdaki sınırlamaları vardır:

- Yalnızca geçerli projenin dışında tanımlanan özel denetimler için çalışır.

- Çözüm yapılandırmasını Hata Ayıklama'dan Yayın'a veya Yayın'dan Hata Ayıklama'ya değiştirmiyor. Bunun nedeni, başvuru bir proje başvurusu değil, bunun yerine disk üzerinde derlemeye olandır. Denetim geçerli çözümün parçası ise, Hata Ayıklama'dan Yayın'a değiştir zaman projeniz denetimin Hata Ayıklama sürümüne başvurur.

Ayrıca, tasarım zamanı meta verileri özel denetime uygulanırsa ve bu meta veriler [Microsoft.Windows. Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) olarak `false` ayarlanır, denetim Araç Kutusunda görünmez.

Denetiminiz için ad alanını ve derlemeyi eşlerken denetimlerinize doğrudan XAML görünümünde başvurabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
- [WPF kullanmaya başlama](../../designers/getting-started-with-wpf.md)
