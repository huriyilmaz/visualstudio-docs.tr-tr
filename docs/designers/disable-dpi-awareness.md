---
title: Formlarda ölçekleme için DPı tanımayı devre dışı bırak
description: hdpı izleyicilerinde Windows Form Tasarımcısı ölçeklendirme sorunlarını giderin.
ms.date: 11/30/2021
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.topic: how-to
ms.custon: contperf-fy22q2
ms.openlocfilehash: 582f1046da0a493959acfa8fc59eaac77e80e751
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134553849"
---
# <a name="disable-dpi-awareness-to-address-scaling-issues-with-windows-forms-designer-in-visual-studio"></a>Visual Studio Windows Form Tasarımcısı ölçeklendirme sorunlarını gidermek için dpı tanımayı devre dışı bırakın

bu makalede, hdpı izleyicilerinde Windows Form Tasarımcısı sınırlamaları ve [Visual Studio dpı kullanmayan bir işlem olarak nasıl çalıştıracağınızı](#resolve-hdpi-display-problems)öğreneceksiniz.

Visual Studio, ekran tarafından otomatik olarak ölçeklendirilirken, inç başına nokta (dpı) kullanan bir uygulamadır. Bir uygulama DPı uyumlu değilse, işletim sistemi uygulamayı bir bit eşlem olarak ölçeklendirir. Bu davranışa Ayrıca DPı Sanallaştırması da denir. Uygulama hala %100 ölçeklendirme veya 96 DPI ' da çalıştığını düşünüyor.

Aşağıdakileri de yapabilirsiniz:
+ [Windows Forms otomatik olarak ölçeklendir](/dotnet/framework/winforms/automatic-scaling-in-windows-forms) 
+ [Farklı pikseller içeren ekranlar için Işlemeyi en iyileştirme seçeneğini belirleyin (yeniden başlatma gerektirir)](../ide/reference/general-environment-options-dialog-box.md#visual-experience)

## <a name="scaling-windows-forms-designer-on-hdpi-monitors"></a>ölçeklendirme: hdpı izleyicilerinde Windows Form Tasarımcısı

Visual Studio **Windows Form Tasarımcısı** ölçeklendirme desteği yok. bu, yüksek nokta başına (hdpi) izleyicilerinde **Windows Form Tasarımcısı** bazı formları açtığınızda sorunları görüntüler. Örnekler için aşağıdaki görüntüde gösterildiği gibi denetimler örtüşme gibi görünebilir:

![hdpı izleyici üzerinde Windows Form Tasarımcısı](./media/win-forms-designer-hdpi.png)

bir hdpı izleyicisinde Visual Studio **Windows Form Tasarımcısı** bir form açtığınızda Visual Studio tasarımcının en üstünde sarı bir bilgi çubuğu görüntüler:

![dpı duyarsız modda yeniden başlatmak için Visual Studio bilgi çubuğu](./media/scaling-gold-bar.png)

**Ana görüntüinizdeki ölçeklendirmeyi okuyan ileti, %200 (192 DPI) olarak ayarlanmıştır. Bu, tasarımcı penceresinde işleme sorunlarına neden olabilir.**

> [!NOTE]
> bu bilgi çubuğu Visual Studio 2017 sürüm 15,8 ' de kullanıma sunulmuştur.

Tasarımcıda çalışmıyorsanız ve formunuzun yerleşimini ayarlamanız gerekmiyorsa, bilgi çubuğunu yoksayabilirsiniz ve kod düzenleyicisinde veya diğer tasarımcı türlerinde çalışmaya devam edebilirsiniz. (Bilgi çubuğu görünmeye devam etmeden de [bildirimleri devre dışı](#disable-notifications) bırakabilirsiniz.) yalnızca **Windows Form Tasarımcısı** etkilenir. **Windows Form Tasarımcısı** çalışmanız gerekiyorsa, sonraki bölümde [sorunu çözmenize](#resolve-hdpi-display-problems)yardımcı olur.

## <a name="resolve-hdpi-display-problems"></a>HDPı görüntüleme sorunlarını çözme

Görüntü sorununu çözmek için üç seçenek vardır:

- [dpı kullanmayan bir işlem olarak Visual Studio yeniden başlatın](#restart-visual-studio-as-a-dpi-unaware-process)
- [Kayıt defteri girişi ekleme](#add-a-registry-entry)
- [Görüntü ölçeklendirme ayarınızı %100 olarak ayarlayın](#set-your-display-scaling-setting-to-100)

> [!TIP]
> Ayarları komut satırından yönetmeyi tercih ediyorsanız, [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) `/noscale` %100 ölçeklendirme modunda çalıştırmak için bir komut satırı parametresi olarak alır.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>dpı kullanmayan bir işlem olarak Visual Studio yeniden başlatın

sarı bilgi çubuğu 'ndaki seçeneği belirleyerek Visual Studio dpı kullanmayan bir işlem olarak yeniden başlatabilirsiniz. Bu, sorunu çözmenin tercih edilen yoludur.

Visual Studio, dpı kullanmayan bir işlem olarak çalıştığında, tasarımcı düzeni sorunları çözümlenir, ancak yazı tipleri bulanık görünebilir. Visual Studio, Visual Studio dpı kullanmayan bir işlem olarak çalıştığını bildiren, dpı kullanmayan bir işlem olarak çalıştırıldığında farklı bir sarı bilgilendirici ileti görüntüler **. WPF ve XAML tasarımcıları doğru görüntülenmeyebilir.** bilgi çubuğu, **Visual Studio dpı kullanan bir işlem olarak yeniden başlatma** seçeneği de sağlar.

> [!NOTE]
> - dpı kullanmayan bir işlem olarak yeniden başlatma seçeneğini belirlediğinizde Visual Studio yerleşik araç pencereleri varsa, bu araç pencerelerinin konumu değişebilir.
> - varsayılan Visual Basic profilini kullanıyorsanız veya **araçlar** seçenekler projelerinde ve çözümlerinde **oluşturulan yeni projeleri kaydet** seçeneği işaretli değilse  >    >  , Visual Studio dpı kullanmayan bir işlem yeniden başlatıldığında projenizi yeniden açamazsınız. Ancak, projeyi   >  **en son projeler ve çözümler** altında seçerek açabilirsiniz.

**Windows Form Tasarımcısı** çalışmayı bitirdiğinizde Visual Studio dpı kullanan bir işlem olarak yeniden başlatmanız önemlidir. DPı kullanmayan bir işlem çalışırken, yazı tipleri bulanık görünebilir ve **XAML Tasarımcısı** gibi diğer tasarımcılarda sorunlar görebilirsiniz. Visual Studio, dpı kullanmayan modda çalışırken kapatıp yeniden açarsanız, dpı uyumlu hale gelir. bilgi çubuğunda **dpı kullanan bir işlem seçeneği olarak Visual Studio yeniden başlat** ' ı da seçebilirsiniz.

### <a name="add-a-registry-entry"></a>Kayıt defteri girişi ekleme

kayıt defterini değiştirerek Visual Studio dpı duyarsız olarak işaretleyebilirsiniz. **Kayıt defteri Düzenleyicisi 'ni** açın ve **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** alt anahtarına bir giriş ekleyin:

**giriş**: Visual Studio 2017, 2019 veya 2022 ' ı kullanıp kullanmayacağınızı bağlı olarak, şu değerlerden birini kullanın:

- C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe
- C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Visual Studio Professional veya Enterprise sürümünü kullanıyorsanız, **Community** , girişte **Professional** veya **Enterprise** ile değiştirin. Ayrıca, sürücü harfini gereken şekilde değiştirin.

**Tür**: REG_SZ <br>
**Değer**: dpiduyarsız

> [!NOTE]
> Visual Studio, kayıt defteri girişini kaldırana kadar dpı duyarsız modda kalır.

### <a name="set-your-display-scaling-setting-to-100"></a>Görüntü ölçeklendirme ayarınızı %100 olarak ayarlayın

görüntü ölçeklendirme ayarınızı Windows 10% 100 olarak ayarlamak için, görev çubuğu arama kutusunda **ekran ayarları** yazın ve ardından **görüntü ayarlarını değiştir**' i seçin. **Ayarlar** penceresinde **metin, uygulamalar ve diğer öğelerin boyutunu** **%100** olarak değiştirin.

Ekran ölçeklendirmesinin %100 olarak ayarlanması, Kullanıcı arabirimini kullanılabilir hale getirmek için çok küçük hale gösterebileceğinden, istenmeyen bir durum olabilir.

## <a name="disable-notifications"></a>Bildirimleri devre dışı bırak

Visual Studio DPı ölçeklendirme sorunları hakkında bildirim almak zorunda değilsiniz seçeneğini belirleyebilirsiniz. Örneğin, tasarımcıda çalışmıyorsanız bildirimleri devre dışı bırakmak isteyebilirsiniz.

Bildirimleri devre dışı bırakmak için:
1.   >  **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin. 
2. **Windows Form Tasarımcısı**  >  **genel**' i seçin ve **dpı ölçeklendirme bildirimleri** ' ni **False** olarak ayarlayın.

![Visual Studio DPı ölçeklendirme bildirimleri seçeneği](./media/notifications-option.png)

Ölçeklendirme bildirimlerini daha sonra yeniden etkinleştirmek istiyorsanız, özelliği **true** olarak ayarlayın.

## <a name="troubleshoot"></a>Sorun giderme

dpı tanıma geçişi Visual Studio beklendiği gibi çalışmıyorsa, `dpiAwareness` kayıt defteri düzenleyicisi 'nde **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** alt anahtarında değerin olup olmadığını denetleyin. Varsa değeri silin.
