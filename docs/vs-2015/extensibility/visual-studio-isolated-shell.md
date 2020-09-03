---
title: Visual Studio yalıtılmış Kabuğu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef2d1cbffab5e38e603b0e50beb896f1c6efa23d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919200"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Yalıtılmış Kabuğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio yalıtılmış Kabuğu, Visual Studio 'nun diğer sürümleriyle yan yana çalışabilen tek başına uygulamalar oluşturmanıza olanak tanır. Birincil olarak, Visual Studio Hizmetleri 'ni kullanan, ancak özelleştirilmiş bir görünüm ve marka içeren özelleştirilmiş araçları barındırmak için kullanılır. Visual Studio özellikleri ve menü komut grupları kolayca açılıp kapatılabilir. Uygulama başlıkları, uygulama simgeleri ve giriş ekranları tamamen özelleştirilebilir. Özelleştirilebilir özelliklerin listesi için bkz. [yalıtılmış Kabuğu özelleştirme](../extensibility/customizing-the-isolated-shell.md).  
  
 Yalıtılmış bir kabuk projesiyle çalışmak için Visual Studio SDK 'sını yüklemelisiniz. Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Yalıtılmış bir kabuk uygulaması oluşturmak için Visual Studio Kabuğu yalıtılmış projesi ile başlayın. Bu proje, yalıtılmış Kabuk uygulamanızı geliştirmek ve test etmek için gereken her şeyi içerir. Uygulamanızı dağıtan Kurulum programını yazmaya hazırsanız, [Microsoft Visual Studio Kabuğu (yalıtılmış) yeniden dağıtılabilir paketten](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)yalıtılmış Kabuk yeniden dağıtılabilir paketini almanız gerekir.  
  
> [!NOTE]
> Yalıtılmış Kabuk yeniden dağıtılabilir paketine erişebilmek için önce kısa bir Müşteri anketi doldurmanız istenir.  Anketi doldurduktan sonra, yeniden dağıtılabilir paket indirme bağlantıları içeren bir Visual Studio Connect sayfasına yönlendirilirsiniz.  Yükleme bağlantılarını, Visual Studio **2015 TÜMLEŞIK ve YALıTıLMıŞ kabuk sekmesindeki programlar &#124;** Visual Studio Connect sitesine sonraki ziyaretlerde bulabilirsiniz.  
  
> [!NOTE]
> Yalıtılmış kabuk tabanlı bir uygulamanın nasıl dağıtılacağı hakkında daha fazla bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Yalıtılmış kabuğa göre çalışma  
 Visual Studio yalıtılmış Kabuk uygulamasının, Visual Studio Hizmetleri 'ne tam erişimi vardır ve özel özelleştirmeyi ve markalamayı destekler. Yalıtılmış bir kabuk uygulamasını özelleştirebileceğiniz çeşitli yollar vardır:  
  
- Yalıtılmış bir kabuk uygulamasını başka bir Visual Studio uzantısında kullandığınız gibi genişletmek için VSPackages ve Managed Extensibility Framework (MEF) bileşen parçalarını kullanabilirsiniz. Daha fazla bilgi için bkz. [yalıtılmış Kabuğu genişletme](../extensibility/extending-the-isolated-shell.md).  
  
- Visual Studio özelliklerini ve menü komut gruplarını kullanılabilir veya kullanılamaz hale getirmek için, uygulamanın kullanıcı arabirimi (UI) projesindeki. vsct dosyasını güncelleştirin.  
  
- **Seçenek** sayfalarını veya diğer Visual Studio Kabuğu bileşenlerini uygulamadan kaldırmak için, uygulamanın. pkgundef dosyasını güncelleştirin.  
  
- Kabuğun görünümü veya davranışının diğer yönlerini değiştirmek için, uygulamanın. pkgdef dosyasını güncelleştirin.  
  
- Kabuğun bazı yönleri de uygulama başlatıldığında belirtilebilir. Bunu yapmak için, çağrısındaki parametreleri appenvstub.dll başlangıç giriş noktasına güncelleştirin.  
  
  Özelleştirebileceğiniz farklı öğeler hakkında daha fazla bilgi için bkz. [yalıtılmış kabuğun öğeleri](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Yalıtılmış kabuğun standart özellikleri  
 Aşağıdaki özellikler, tüm Visual Studio sürümleri için standarttır.  
  
|Özellik kategorisi|Öne çıkan özelliği|  
|----------------------|-------------|  
|IDE özellikleri|İçeri/dışarı aktarma ayarları<br /><br /> Araç kutusu denetim yükleyicisi<br /><br /> Görev Listesi & Hata Listesi<br /><br /> Çıktı Penceresi<br /><br /> Başlangıç Sayfası<br /><br /> Özellikler Penceresi<br /><br /> Araç Kutusu<br /><br /> Çözüm Gezgini<br /><br /> Yer işareti penceresi<br /><br /> Sınıf Görünümü<br /><br /> Nesne Tarayıcısı<br /><br /> Komut Penceresi<br /><br /> Belge Anahattı<br /><br /> Kaynak Görünümü<br /><br /> Dış araç<br /><br /> Windows Communication Foundation (WCF) Hizmet Başvurusu Ekle<br /><br /> Dil ile tümleşik sorgu (LINQ) desteği|  
|Düzenleyici/tasarımcı|Kod gözatma araçları (Birleşik bul, kaynak tanımı, devralma)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Kod parçacıkları Yöneticisi<br /><br /> Kod Parçacıkları<br /><br /> Yeniden Düzenle<br /><br /> Düzgün listeleme<br /><br /> IntelliSense filtreleme<br /><br /> Kod tanımı penceresi<br /><br /> Uygulama Tasarımcısı<br /><br /> Windows Form Tasarımcısı<br /><br /> Windows Presentation Foundation (WPF) Tasarımcısı|  
|Hata Ayıklama|C# ifade değerlendiricisi<br /><br /> Yerel hata ayıklama<br /><br /> Yönetilen hata ayıklama<br /><br /> Düzenle ve Devam Et<br /><br /> Çapraz iş parçacığı hata ayıklaması<br /><br /> Görsel öğeler<br /><br /> DataTips<br /><br /> Yerel hata ayıklama<br /><br /> Betik hata ayıklaması<br /><br /> Birlikte çalışma hata ayıklaması<br /><br /> Tam zamanında (JıT) hata ayıklama<br /><br /> Çok işlemli hata ayıklama<br /><br /> XSLT hata ayıklama<br /><br /> Yerel İşleme İliştir<br /><br /> İzleme noktaları<br /><br /> Kesme noktası kısıtlamaları|  
|Veriler|Sunucu Gezgini (yalnızca Basitleştirilmiş-veri)<br /><br /> Yerel verilere veri bağlama (. MDF veya. TATIL<br /><br /> Nesneye veri bağlama<br /><br /> Web hizmetine veri bağlama<br /><br /> Tam veri denetimleri kümesi<br /><br /> XML düzenleyicisi<br /><br /> Yerel veritabanı sunucusuna veri bağlama<br /><br /> Veri Kaynakları penceresi|  
|Web|HTML Düzenleyicisi<br /><br /> Web Tarayıcısı<br /><br /> Web Forms Tasarımcısı<br /><br /> Web sitesi projesi<br /><br /> Web uygulaması projesi|  
|Genişletilebilirlik|VSPackages ve MEF bileşenlerini kullanır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kabuk (Yalıtılmış veya Tümleşik)](../extensibility/shell-isolated-or-integrated.md)
