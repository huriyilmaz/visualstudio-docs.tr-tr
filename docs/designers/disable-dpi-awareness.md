---
title: DPI farkındalığını Visual Studio
description: HDPI monitörleri üzerinde Windows Form Tasarımcısı'nın sınırlamalarını ve Visual Studio DPI'den haberdar olmayan bir işlem olarak çalıştırmayı ele alan.
ms.date: 09/28/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.openlocfilehash: 3b4ae4cd215546744172ab64890254c488823e92
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089790"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>DPI farkındalığını Visual Studio

Visual Studio nokta/inç (DPI) farkında olan bir uygulamadır, yani ekran otomatik olarak ölçeklendirilir. Bir uygulama DPI'yi farkında olmadığını belirttiyse, işletim sistemi uygulamayı bit eşlem olarak ölçeklendirir. Bu davranış DPI sanallaştırması olarak da bilinir. Uygulama hala %100 ölçeklendirme veya 96 dpi'de çalışıyor olduğunu düşünür.

Bu makalede, HDPI monitörleri üzerinde Windows Forms Tasarımcısı'nın sınırlamaları ve DPI'Visual Studio olmayan bir işlem olarak nasıl çalıştırılları tartıştır.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Windows HDPI monitörlerde Form Tasarımcısı

Windows **Forms Tasarımcısı Visual Studio** ölçeklendirme desteğine sahip değil. Bu, formlardan bazılarını inç başına yüksek nokta (HDPI) **Windows** Form Tasarımcısı'nda a açılışta görüntü sorunlarına neden olur. Örnekler için, denetimler aşağıdaki görüntüde gösterildiği gibi çakışıyor gibi görünebilir:

![Windows HDPI izleyicisi üzerinde Form Tasarımcısı](./media/win-forms-designer-hdpi.png)

**HDPI** izleyicisinde Windows Form Tasarımcısı'nda Visual Studio bir form Visual Studio tasarımcının en üstünde sarı bir bilgilendirme çubuğu görüntüler:

![DPI'Visual Studio modunda yeniden başlatılacak olan bilgi çubuğu](./media/scaling-gold-bar.png)

İleti ana görüntüde **ölçeklendirme %200'e (192 dpi) ayarlanmıştır. Bu, tasarımcı penceresinde işleme sorunlarına neden olabilir.**

> [!NOTE]
> Bu bilgi çubuğu, 2017 Visual Studio 15.8 sürümünde tanıtıldı.

Tasarımcıda çalışmıyorsanız ve form düzeninizi ayarlamanıza gerek yoksa, bilgi çubuğunu yoksayabilir ve kod düzenleyicisinde veya diğer tasarımcı türlerinde çalışmaya devam edin. (Bildirim [çubuğunun görünmeye](#disable-notifications) devam etmeyilmesi için bildirimleri de devre dışı abilirsiniz.) Yalnızca **Windows Forms Tasarımcısı** etkilenir. **Windows Forms Designer'da** çalışmanıza gerek yoksa, sonraki bölüm sorunu [çözmenize yardımcı olur.](#to-resolve-the-display-problem)

## <a name="to-resolve-the-display-problem"></a>Görüntüleme sorununu çözmek için

Görüntüleme sorununu çözmek için üç seçenek vardır:

- [DPI Visual Studio işlemi olarak yeniden başlatma](#restart-visual-studio-as-a-dpi-unaware-process)
- [Kayıt defteri girişi ekleme](#add-a-registry-entry)
- [Görüntü ölçeklendirme ayarınızı %100 olarak ayarlayın](#set-your-display-scaling-setting-to-100)

> [!TIP]
> Ayarları komut satırıyla yönetmeyi tercih ederseniz, [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) %100 ölçeklendirme modunda çalıştırmak için komut `/noscale` satırı parametresi olarak alır.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>DPI'Visual Studio olmayan bir işlem olarak yeniden başlatın

Sarı bilgi Visual Studio seçeneğini kullanarak DPI'den haberdar olmayan bir işlem olarak yeniden başlatabilirsiniz. Bu, sorunu çözmenin tercih edilen yoludur.

Bu Visual Studio DPI'den haberdar olmayan bir işlem olarak çalıştırılana kadar tasarımcı düzeni sorunları çözülür, ancak yazı tipleri bulanık görünebilir. Visual Studio, DPI'yi farksız bir işlem olarak çalıştırarak DPI'den haberdar olmayan bir işlem olarak Visual Studio farklı bir sarı bilgilendirme **iletisi görüntüler. WPF ve XAML tasarımcıları doğru görüntülenmez.** Bilgi çubuğu ayrıca DPI'yi kullanarak **Visual Studio yeniden başlatma seçeneği de sağlar.**

> [!NOTE]
> - DPI'den haberdar olmayan bir işlem olarak yeniden başlatma seçeneğini Visual Studio aracı pencerelerini takmadıysanız, bu araç pencerelerinin konumu değişebilir.
> - Varsayılan Visual Basic profilini kullanırsanız veya Araçlar Seçenekler Projeleri  ve Çözümler'de Yeni projeleri oluşturulduğunda kaydet seçeneğinin seçimi kaldırılırsa  >    >  Visual Studio, DPI'den haberdar olmayan bir işlem olarak yeniden başlatıldığında projenizi yeniden açamaz. Ancak, Projeyi Dosya Son Projeler ve Çözümler altında  >  **seçerek açabilirsiniz.**

Windows Forms Tasarımcısı'nda Visual Studio DPI'ye sahip bir işlem olarak yeniden **başlatmak önemlidir.** DPI'den haberdar olmayan bir işlem olarak çalışan yazı tipleri bulanık görünür ve diğer tasarımcılarda örneğin, **XAML Tasarımcısı.** DPI'Visual Studio modunda çalıştırılan bir dosyayı kapatıp yeniden açarsanız DPI'yi tekrar fark eden bir hale gelir. Bilgi çubuğunda **DPI'Visual Studio işlem olarak yeniden** başlat seçeneğini de belirleyin.

### <a name="add-a-registry-entry"></a>Kayıt defteri girişi ekleme

Kayıt defterini Visual Studio DPI'den haberdar değil olarak işaret değiştirebilirsiniz. Kayıt **Defteri Düzenleyicisi'ni** açın veHKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers **ekleyin:**

**Girdi:** 2017 veya 2019 Visual Studio kullandığınıza bağlı olarak şu değerlerden birini kullanın:

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Visual Studio'nin Professional veya Enterprise sürümünü kullanıyorsanız, Community yerine **Professional** **veya** **Enterprise** girin. Ayrıca sürücü harfini de gereken şekilde değiştirin.

**Tür**: REG_SZ

**Değer:** DPIUNAWARE

> [!NOTE]
> Visual Studio kayıt defteri girdisini kaldırana kadar DPI'den haberdar olmayan modda kalır.

### <a name="set-your-display-scaling-setting-to-100"></a>Görüntü ölçeklendirme ayarınızı %100 olarak ayarlayın

Görüntü ölçeklendirme ayarınızı %100 olarak ayarlamak Windows 10 görev  çubuğu arama kutusuna görüntü ayarlarını yazın ve ardından Görüntü ayarlarını **değiştir'i seçin.** Ayarlar **penceresinde** Metin, **uygulama ve** diğer öğelerin boyutunu **%100** olarak ayarlayın.

Kullanıcı arabiriminin kullanılabilir olması için çok küçük olduğundan, görüntü ölçeklendirmenizi %100'e ayarlamanız istenmeyen bir durum olabilir.

## <a name="disable-notifications"></a>Bildirimleri devre dışı bırakma

DPI ölçeklendirme sorunları hakkında daha fazla bilgi Visual Studio. Örneğin tasarımcıda çalışmıyorsanız bildirimleri devre dışı bırakmak iyi olabilir.

Bildirimleri devre dışı bırakmak için Araçlar  >  **Seçenekleri'ne** tıklayın ve Seçenekler **iletişim kutusunu** açın. Ardından, **Windows Forms Tasarımcısı**  >  **Genel'i seçin** ve **DPI Ölçeklendirme Bildirimleri'yi** False olarak **ayarlayın.**

![Visual Studio'de DPI ölçeklendirme bildirimleri seçeneği](./media/notifications-option.png)

Ölçeklendirme bildirimlerini daha sonra yeniden canlanabilir hale gelecek şekilde ayarlamak için özelliğini True olarak **ayarlayın.**

## <a name="troubleshoot"></a>Sorun giderme

DPI tanıma geçişi bu geçişte beklendiği gibi Visual Studio Kayıt Defteri Düzenleyicisi'ndeHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exeolup `dpiAwareness` olmadığını kontrol edin.  Varsa değeri silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta otomatik ölçeklendirme](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
