---
title: Visual Studio'da DPI farkındalığını devre dışı
description: WINDOWS Forms Designer'ın HDPI monitörlerde sınırlamalarını ve Visual Studio'nun DPI'dan habersiz bir işlem olarak nasıl çalıştırılabildiğini tartışır.
ms.date: 04/05/2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: 8e7a5a5871b66fd388d7c5a9f774a22163d06729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589571"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Visual Studio'da DPI farkındalığını devre dışı

Visual Studio, ekran otomatik olarak ölçeklendirilir anlamına gelir inç başına bir nokta (DPI) farkında uygulamavardır. Bir uygulama DPI'ya duyarlı olmadığını belirtirse, işletim sistemi uygulamayı bit eşlemi olarak ölçeklendirin. Bu davranış, DPI sanallaştırma olarak da adlandırılır. Uygulama hala% 100 ölçekleme, ya da 96 dpi çalıştığını düşünüyor.

Bu makalede, HDPI monitörlerde Windows Forms Designer sınırlamaları ve DPI-habersiz bir işlem olarak Visual Studio çalıştırmak için nasıl anlatılmaktadır.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>HDPI monitörlerde Windows Forms Designer

Visual Studio'daki **Windows Forms Designer'ın** ölçekleme desteği yoktur. Bu, **Windows Forms Designer'da** inç başına yüksek noktalar (HDPI) monitörlerde bazı formları açtığınızda görüntü sorunlarına neden olur. Örneğin, denetimler aşağıdaki resimde gösterildiği gibi çakışıyor gibi görünebilir:

![HDPI monitörde Windows Forms Designer](./media/win-forms-designer-hdpi.png)

Visual Studio'daki **Windows Forms Designer'da** bir HDPI monitörde bir form açtığınızda, Visual Studio tasarımcının üst kısmında sarı bir bilgi çubuğu görüntüler:

![DPI-habersiz modunda yeniden başlatmak için Visual Studio'da Bilgilendirme çubuğu](./media/scaling-gold-bar.png)

İleti, **ana ekranınızdaki Ölçekleme'nin %200 olarak ayarlanır (192 dpi) olarak ayarlanır. Bu, tasarımcı penceresinde işleme sorunlarına neden olabilir.**

> [!NOTE]
> Bu bilgilendirme çubuğu Visual Studio 2017 sürüm 15.8'de tanıtıldı.

Tasarımcıda çalışmıyorsanız ve formunuzun düzenini ayarlamanız gerekmiyorsa, bilgi çubuğunu yoksayabilir ve kod düzenleyicisinde veya diğer tasarımcı türlerinde çalışmaya devam edebilirsiniz. (Bilgi çubuğunun görünmeye devam etmesi için [bildirimleri](#disable-notifications) de devre dışı bekleyebilirsiniz.) Yalnızca **Windows Forms Designer** etkilenir. **Windows Forms Designer'da**çalışmanız gerekiyorsa, bir sonraki bölüm [sorunu çözmenize](#to-resolve-the-display-problem)yardımcı olur.

## <a name="to-resolve-the-display-problem"></a>Görüntü sorununu çözmek için

Görüntü sorununu çözmek için üç seçenek vardır:

- [Visual Studio'u DPI'den habersiz bir işlem olarak yeniden başlatın](#restart-visual-studio-as-a-dpi-unaware-process)
- [Kayıt defteri girişi ekleme](#add-a-registry-entry)
- [Ekran ölçekleme ayarınızı %100'e ayarlama](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Visual Studio'u DPI'den habersiz bir işlem olarak yeniden başlatın

Sarı bilgi çubuğundaki seçeneği seçerek Visual Studio'yu DPI'dan habersiz bir işlem olarak yeniden başlatabilirsiniz. Bu sorunu çözmek için tercih edilen yoludur.

Visual Studio DPI'dan habersiz bir işlem olarak çalıştığında, tasarımcı düzeni sorunları çözülür, ancak yazı tipleri bulanık görünebilir. Visual Studio, **Visual Studio'nun DPI'den habersiz bir işlem olarak çalıştığını ve Visual Studio'nun DPI'dan habersiz bir işlem olarak çalıştığını söyleyen farklı bir sarı bilgi iletisi görüntüler. WPF ve XAML tasarımcıları doğru görüntülemeyebilir.** Bilgilendirme çubuğu ayrıca **Visual Studio'yu DPI'ya duyarlı bir işlem olarak yeniden başlatma**seçeneği de sunar.

> [!NOTE]
> - DPI'dan habersiz bir işlem olarak yeniden başlatma seçeneğini seçtiğinizde Visual Studio'da yerleşik araç pencereniz varsa, bu araç pencerelerinin konumu değişebilir.
> - Varsayılan Visual Basic profilini kullanıyorsanız veya **Araçlar** > **Seçenekleri** > **Projeleri ve Çözümleri'nde**oluşturulan seçenek **seçildiğinde yeni projeleri kaydet** varsa, Visual Studio, DPI'dan habersiz bir işlem olarak yeniden başlatıldığında projenizi yeniden açamaz. Ancak, **Dosya** > **Son Projeler ve Çözümleri**altında seçerek proje açabilirsiniz.

**Windows Forms Designer'da**çalışmayı bitirdiğinizde Visual Studio'yu DPI'ya duyarlı bir işlem olarak yeniden başlatmak önemlidir. DPI'dan habersiz bir işlem olarak çalışırken, yazı tipleri bulanık görünebilir ve **XAML Designer**gibi diğer tasarımcılarda sorunlar görebilirsiniz. DpI'dan habersiz modda çalışırken Visual Studio'u kapatıp yeniden açarsanız, yeniden DPI'ya duyarlı hale gelir. Ayrıca, bilgi çubuğunda **DPI'ya duyarlı işlem** seçeneği olarak Görsel Stüdyoyu Yeniden Başlat'ı da tıklatabilirsiniz.

### <a name="add-a-registry-entry"></a>Kayıt defteri girişi ekleme

Kayıt defterini değiştirerek Visual Studio'yu DPI'dan habersiz olarak işaretleyebilirsiniz. **Kayıt Defteri Düzenleyicisi'ni** açın ve **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** alt anahtarına bir giriş ekleyin:

**Giriş**: Visual Studio 2017 veya 2019'u kullanıp kullanmadığınıza bağlı olarak aşağıdaki değerlerden birini kullanın:

- C:\Program Dosyaları (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Dosyaları (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Visual Studio'nun Professional veya Enterprise baskısını kullanıyorsanız, girişte **Topluluk'u** **Professional** veya **Enterprise** ile değiştirin. Ayrıca sürücü harfini gerektiği gibi değiştirin.

**Tür**: REG_SZ

**Değer**: DPIUNAWARE

> [!NOTE]
> Kayıt defteri girişini kaldırana kadar Visual Studio DPI'dan habersiz modunda kalır.

### <a name="set-your-display-scaling-setting-to-100"></a>Ekran ölçekleme ayarınızı %100'e ayarlama

Windows 10'da ekran ölçekleme ayarınızı %100 olarak ayarlamak için görev çubuğu arama kutusuna **ekran ayarları** yazın ve ardından **ekran ayarlarını değiştir'i**seçin. **Ayarlar** penceresinde, **metin, uygulama ve diğer öğelerin boyutunu** **%100**olarak değiştir'i ayarlayın.

Kullanıcı arabirimini kullanılabilir olamayacak kadar küçük hale getirebileceğinden, ekran ölçeklemenizi %100'e ayarlamak istenmeyen bir şey olabilir.

## <a name="disable-notifications"></a>Bildirimleri devre dışı

Visual Studio'da DPI ölçekleme sorunları hakkında bilgilendirilmemeyi seçebilirsiniz. Örneğin, tasarımcıda çalışmıyorsanız bildirimleri devre dışı kılabilir.

Bildirimleri devre dışı kalmak için **Seçenekler** iletişim kutusunu açmak için **Araçlar** > **Seçenekleri'ni** seçin. Ardından, **Windows Forms Designer** > **Genel'i**seçin ve **DPI Ölçekleme Bildirimlerini** **False**olarak ayarlayın.

![Visual Studio'da DPI ölçekleme bildirimleri seçeneği](./media/notifications-option.png)

Daha sonra ölçekleme bildirimlerini yeniden etkinleştirmek istiyorsanız, özelliği **True**olarak ayarlayın.

## <a name="troubleshoot"></a>Sorun giderme

DPI-farkındalık geçişi Visual Studio'da beklendiği gibi çalışmıyorsa, Kayıt `dpiAwareness` Defteri Düzenleyicisi'ndeki **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** alt anahtarındaki değere sahip olup olmadığınızı kontrol edin. Varsa değeri silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Formlarında otomatik ölçekleme](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
