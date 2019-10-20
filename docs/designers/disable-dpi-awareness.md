---
title: Visual Studio 'da DPı tanımayı devre dışı bırak
description: HDPı izleyicilerinde Windows Form Tasarımcısı sınırlamaları ve Visual Studio 'Yu DPı kullanmayan bir işlem olarak çalıştırmayı açıklar.
ms.date: 04/05/2019
author: jillre
ms.author: jillfra
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: a368108f1b8f9682151ed8c7b0a6d8b83b1b8a1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637403"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Visual Studio 'da DPı tanımayı devre dışı bırak

Visual Studio, bir nokta/inç (DPI) uyumlu uygulama (yani, ekran otomatik olarak ölçeklendirilebilen bir uygulamadır). Bir uygulama DPı uyumlu değilse, işletim sistemi uygulamayı bir bit eşlem olarak ölçeklendirir. Bu davranışa Ayrıca DPı Sanallaştırması da denir. Uygulama hala %100 ölçeklendirme veya 96 DPI ' da çalıştığını düşünüyor.

Bu makalede, HDPı izleyicilerinde Windows Form Tasarımcısı sınırlamaları ve Visual Studio 'nun DPı kullanmayan bir işlem olarak çalıştırılması açıklanmaktadır.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>HDPı izleyicilerinde Windows Form Tasarımcısı

Visual Studio 'daki **Windows Form Tasarımcısı** ölçeklendirme desteği yoktur. Bu, yüksek nokta başına (HDPI) izleyicilerinde **Windows Form Tasarımcısı** bazı formları açtığınızda sorunları görüntüler. Örnekler için aşağıdaki görüntüde gösterildiği gibi denetimler örtüşme gibi görünebilir:

![HDPı izleyici üzerinde Windows Form Tasarımcısı](./media/win-forms-designer-hdpi.png)

Visual Studio 'da bir HDPı izleyicisinde **Windows Form Tasarımcısı** form açtığınızda, Visual Studio tasarımcının en üstünde sarı bir bilgi çubuğu görüntüler:

![Visual Studio 'da DPı kullanmayan modda yeniden başlatılacak bilgi çubuğu](./media/scaling-gold-bar.png)

**Ana görüntüinizdeki ölçeklendirmeyi okuyan ileti, %200 (192 DPI) olarak ayarlanmıştır. Bu, tasarımcı penceresinde işleme sorunlarına neden olabilir.**

> [!NOTE]
> Bu bilgi çubuğu, Visual Studio 2017 sürüm 15,8 ' de eklenmiştir.

Tasarımcıda çalışmıyorsanız ve formunuzun yerleşimini ayarlamanız gerekmiyorsa, bilgi çubuğunu yoksayabilirsiniz ve kod düzenleyicisinde veya diğer tasarımcı türlerinde çalışmaya devam edebilirsiniz. (Bilgi çubuğu görünmeye devam etmeden de [bildirimleri devre dışı](#disable-notifications) bırakabilirsiniz.) Yalnızca **Windows Form Tasarımcısı** etkilenir. **Windows Form Tasarımcısı**çalışmanız gerekiyorsa, sonraki bölümde [sorunu çözmenize](#to-resolve-the-display-problem)yardımcı olur.

## <a name="to-resolve-the-display-problem"></a>Görüntü sorununu çözmek için

Görüntü sorununu çözmek için üç seçenek vardır:

- [Visual Studio 'Yu DPı kullanmayan bir işlem olarak yeniden Başlat](#restart-visual-studio-as-a-dpi-unaware-process)
- [Kayıt defteri girişi ekleme](#add-a-registry-entry)
- [Görüntü ölçeklendirme ayarınızı %100 olarak ayarlayın](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Visual Studio 'Yu DPı kullanmayan bir işlem olarak yeniden Başlat

Sarı bilgi çubuğu 'ndaki seçeneği belirleyerek Visual Studio 'Yu DPı kullanmayan bir işlem olarak yeniden başlatabilirsiniz. Bu, sorunu çözmenin tercih edilen yoludur.

Visual Studio, DPı kullanmayan bir işlem olarak çalıştırıldığında tasarımcı düzeni sorunları çözümlenir, ancak yazı tipleri bulanık görünebilir. Visual Studio **, Visual Studio 'NUN DPI kullanmayan bir işlem olarak çalıştığını bildiren, DPI kullanmayan bir işlem olarak çalıştırıldığında, farklı bir sarı bilgilendirici ileti görüntüler. WPF ve XAML tasarımcıları doğru görüntülenmeyebilir.** Bilgi çubuğu, **Visual Studio 'YU DPI kullanan bir işlem olarak yeniden başlatma**seçeneği de sunar.

> [!NOTE]
> - DPı kullanmayan bir işlem olarak yeniden başlatma seçeneğini belirlediğinizde Visual Studio 'da yerleştirilmemiş araç pencereleri varsa, bu araç pencerelerinin konumu değişebilir.
> - Varsayılan Visual Basic profilini kullanıyorsanız veya **araçlar**  > **Seçenekler**  > **Projeler ve çözümler**' de **oluşturulan yeni projeleri kaydet** seçeneği işaretli değilse, Visual Studio projenizi yeniden açamazsınız DPı kullanmayan bir işlem olarak yeniden başlatılır. Ancak, projeyi **dosya**  > **son projeler ve çözümler**altında seçerek açabilirsiniz.

**Windows Form Tasarımcısı**çalışmayı bitirdiğinizde Visual STUDIO 'yu DPI kullanan bir işlem olarak yeniden başlatmanız önemlidir. DPı kullanmayan bir işlem çalışırken, yazı tipleri bulanık görünebilir ve **XAML Tasarımcısı**gibi diğer tasarımcılarda sorunlar görebilirsiniz. Visual Studio 'Yu, DPı kullanmayan modda çalışırken kapatıp yeniden açarsanız, bu, DPı uyumlu hale gelir. Bilgi çubuğunda, **Visual Studio 'YU DPI kullanan bir işlem olarak yeniden Başlat** seçeneği de tıklayabilirsiniz.

### <a name="add-a-registry-entry"></a>Kayıt defteri girişi ekleme

Kayıt defterini değiştirerek Visual Studio 'Yu DPı duyarsız olarak işaretleyebilirsiniz. **Kayıt defteri Düzenleyicisi 'ni** açın ve **HKEY_CURRENT_USER\Software\Microsoft\Windows Nt\currentversion\appcompatflags\katmanları** alt anahtarına bir giriş ekleyin:

**Giriş**: Visual Studio 2017 veya 2019 ' i kullanıp kullanmayacağınızı bağlı olarak şu değerlerden birini kullanın:

- C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Visual Studio 'nun Professional veya Enterprise sürümünü kullanıyorsanız, **Community** 'Yi girişte **Professional** veya **Enterprise** ile değiştirin. Ayrıca, sürücü harfini gereken şekilde değiştirin.

**Tür**: REG_SZ

**Değer**: dpiduyarsız

> [!NOTE]
> Visual Studio, kayıt defteri girişini kaldırana kadar DPı duyarsız modda kalır.

### <a name="set-your-display-scaling-setting-to-100"></a>Görüntü ölçeklendirme ayarınızı %100 olarak ayarlayın

Ekran ölçeklendirme ayarınızı Windows 10 ' da %100 ' a ayarlamak için, görev çubuğu arama kutusunda **ekran ayarları** yazın ve ardından **görüntü ayarlarını değiştir**' i seçin. **Ayarlar** penceresinde **metin, uygulamalar ve diğer öğelerin boyutunu** **%100**olarak değiştirin.

Ekran ölçeklendirmesinin %100 olarak ayarlanması, Kullanıcı arabirimini kullanılabilir hale getirmek için çok küçük hale gösterebileceğinden, istenmeyen bir durum olabilir.

## <a name="disable-notifications"></a>Bildirimleri devre dışı bırak

Visual Studio 'da DPı ölçeklendirme sorunları hakkında bildirim almak zorunda değilsiniz seçeneğini belirleyebilirsiniz. Örneğin, tasarımcıda çalışmıyorsanız bildirimleri devre dışı bırakmak isteyebilirsiniz.

Bildirimleri devre dışı bırakmak için **Seçenekler** iletişim kutusunu açmak üzere **Araçlar**  > **Seçenekler** ' i seçin. Sonra,**genel** >  **Windows Form Tasarımcısı** seçin ve **DPI ölçeklendirme bildirimlerini** **false**olarak ayarlayın.

![Visual Studio 'da DPı ölçeklendirme bildirimleri seçeneği](./media/notifications-option.png)

Ölçeklendirme bildirimlerini daha sonra yeniden etkinleştirmek istiyorsanız, özelliği **true**olarak ayarlayın.

## <a name="troubleshoot"></a>Sorun giderme

DPı tanıma geçişi, Visual Studio 'da beklendiği gibi çalışmıyorsa, içindeki **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Nt\currentversion\ımage File Execution Options\devenv.exe** alt anahtarında `dpiAwareness` değer olup olmadığını denetleyin. Kayıt Defteri Düzenleyicisi. Varsa değeri silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms otomatik ölçeklendirme](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
