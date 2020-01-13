---
title: Visual Studio Kabuğu (tümleşik) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6220afc2bdf75cc22529c65d5514f5f9e0766555
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919221"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Kabuğu (Tümleşik)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio tümleşik kabuğu, tümleşik geliştirme ortamı (IDE), hata ayıklayıcı ve kaynak denetimi tümleştirmesini içerir. Programlama dili dahil değildir. Ancak Tümleşik Kabuk, programlama dilleri eklemenize olanak sağlayan bir çerçeve sağlar.  
  
 Visual Studio tümleşik kabuğu aslında Visual Studio yalıtılmış Kabuğu ve tümleşik kabuğa özgü bileşenleri içeren ek bir yüklemenin bir birleşimidir.  Tümleşik Kabuk uygulamanız hem yalıtılmış Kabuk yeniden dağıtılabilir paketini hem de [Microsoft Visual Studio Shell yeniden dağıtılabilir paketleri](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)' nden Tümleşik Kabuk yeniden dağıtılabilir paketini de içermelidir.  
  
> [!NOTE]
> Yalıtılmış ve tümleşik kabuk yeniden dağıtılabilir paketlerine erişebilmeniz için önce kısa bir müşteri anketini doldurmanız istenir.  Anketi doldurduktan sonra, yeniden dağıtılabilir paket indirme bağlantılarının olduğu bir Visual Studio Connect sayfasına yönlendirilirsiniz.  Sonraki ziyaretlerde bulunan **Programlar &#124; VISUAL STUDIO 2015 TÜMLEŞIK ve yalıtılmış Kabuk** sekmesinin altındaki Visual Studio Connect sitesine indirme bağlantılarını bulabilirsiniz.  
  
 Tümleşik Kabuk uygulamanızı Visual Studio 'nun tam sürümüyle aynı bilgisayara yüklerseniz, uygulamanızın bileşenleri doğrudan Visual Studio 'ya tümleştirilir.  
  
## <a name="features-in-the-integrated-shell"></a>Tümleşik kabukta Özellikler  
  
|||  
|-|-|  
|Özellik alanı|Özellik|  
|Dil Desteği|-Hiçbiri|  
|IDE|<ul><li>Ayarlar<br /><br /> <ul><li>Ayarları oluştur</li><li>Ayarları içeri ve dışarı aktarma</li><li>Ayarları Sıfırla</li></ul></li><li>**Araç kutusu** tümleştirmesi</li><li>**Görev listesi** tümleştirme</li><li>Yardım tümleştirmesi</li><li>**Seçenekler** iletişim kutusu</li><li>Yazı tipleri ve renkler Yönetimi</li><li>**Çıkış** penceresi</li><li>**Komut** penceresi</li><li>Pencere Yönetimi</li><li>Komutlar, menüler ve tuş bağlamaları</li><li>Etki alanına özgü dil (DSL) çalışma zamanı</li></ul>|  
|Proje sistemi ve proje türleri|-Çözümler ve çözüm klasörleri<br />-Çözüm Yapılandırma Yöneticisi<br />-Öğe yönetimi<br />-Tek projeli ve çoklu proje çözümleri<br />-Uygulama Tasarımcısı (Basitleştirilmiş proje özellikleri)<br />-Web başvurusu Ekle<br />-Hizmet Başvurusu Ekle<br />-Tek projem<br />-Web sitesi proje türleri<br />-Web uygulaması projeleri|  
|{1&gt;Yapı (Build)&lt;1}|-IDE 'de özel derleme adımları<br />-Fikri mülkiyet (IP) koruması için ön derleme<br />-Kod imzalama<br />     MSBuild|  
|Düzenleyici|-Kod gözatma araçları (Birleşik bul, kaynak tanımı, devralma)<br />-Kod gezintisi<br />-IntelliSense<br />-SmartTags<br />-Yeniden düzenleme<br />-Düzgün listeleme<br />-IntelliSense filtreleme<br />-   **kod tanımı** penceresi|  
|Tasarımcı|-Windows Presentation Foundation Tasarımcısı<br />-Windows Form Tasarımcısı<br />-Web Tasarımcısı ve HTML Düzenleyicisi|  
|Veri|-   **Sunucu Gezgini** (Basitleştirilmiş: yalnızca veri). Bkz. Note 1.<br />-   **veri kaynakları** penceresi<br />-Tam veri denetimleri kümesi<br />-XML Düzenleyicisi<br />-Yerel veri kaynağına veri bağlama (. MDF veya. TATIL<br />-Nesneye veri bağlama<br />-Web hizmetine veri bağlama<br />-Yerel veritabanı sunucusuna veri bağlama<br />-Uzak veritabanı sunucusuna veri bağlama<br />-Uzak veriler için DDL araçları<br />-   **Sunucu Gezgini** genişletilebilirlik ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] örnekleri)|  
|Hata Ayıklayıcısı|-Yerel hata ayıklama. Bkz. Note 2.<br />-Yönetilen hata ayıklama<br />-Yerel hata ayıklama<br />-Yerel İşleme İliştir<br />-Uzak işleme iliştir<br />-Anonim temsilci<br />-Uygulama etki alanları<br />-ASPX hata ayıklaması<br />-Öznitelikler<br />-Func-eval sırasında kes<br />-Kesme noktaları<br />-Kesme noktası kısıtlamaları<br />-Callstack<br />-   **komut** penceresi<br />-Çapraz iş parçacığı hata ayıklaması<br />-Veri Ipuçları<br />-Veri görselleştiricisi<br />-Yönetilen hata ayıklama yardımcıları (MDAs) için hata ayıklayıcı desteği<br />-Tür ileticisi için hata ayıklayıcı desteği<br />-OTB için DTEEvents desteği<br />-JMC Stepper<br />-Debugger AppID testi (DBGCLR)<br />-Hata ayıklayıcı profili<br />-Hata ayıklayıcı araçları ve seçenekleri<br />-Hata ayıklama Yineleyici<br />-Tasarım zamanı ifade değerlendirmesi<br />- C# İfade değerlendirici<br />-Ayrıştırılmış derleme<br />-Düzenle ve devam et<br />-Expression değerlendirici pencereleri (Izleme, Yereller, oto)<br />-Özel durum Yardımcısı<br />-Özel durumlar<br />-Yürütme<br />-Genel türler<br />-Doğru kaynak alınıyor<br />-HPC/küme hata ayıklaması<br />-Tümleşik çok dilli hata ayıklama<br />-Birlikte çalışma hata ayıklaması<br />-Tam zamanında hata ayıklama<br />-Yerel hata ayıklama<br />-Yönetilen hata ayıklama<br />-El ile denetim (Işler penceresi)<br />-   Bellek<br />-Mini döküm desteği<br />-Modüller<br />-Çok işlem hata ayıklaması<br />-Yerel hata ayıklama<br />-Yeni hata ayıklama altyapısı desteği<br />-İyileştirilmiş kod hata ayıklaması<br />-Çıktıyı Windows filtrelemesini<br />-Yönetilen hata ayıklama için işlem barındırma<br />-Süreçler<br />-Hızlı Bakış<br />-Yazmaçları<br />-Yığına kayıt yapar<br />-Uzaktan hata ayıklama<br />-Dönüş değerleri<br />-Betik hata ayıklaması<br />-Kaynak hizmeti desteği<br />-Güvenlik<br />Yan yana<br />-SQL<br />-Sembol sunucusu<br />-İzleme noktaları<br />-İş parçacığı<br />-Görselleştirmeler<br />-Genişletilebilir Stil sayfası dil dönüşümleri (XSLT) hata ayıklayıcı|  
|64 bit desteği|-64-hem yönetilen hem de yerel kod için bit hata ayıklama, tüm diller<br />-x64 yerel desteği|  
|Kaynak kodu denetimi (SCC)|-Temel SCC tümleştirmesi. Bkz. Note 3.<br />-Araçlar ve seçenekler doğrulaması|  
|Genişletilebilirlik|-VSPackages ve MEF bileşenlerini tüketme|  
  
## <a name="notes"></a>Notlar  
  
#### <a name="1-data-tools"></a>1. veri araçları  
 Tümleşik Kabuk, veri genişletilebilirlik desteği ve Basitleştirilmiş **Çözüm Gezgini**gibi veritabanı geliştirme araçları içerir. Ancak, SQL Server Express, SQL Raporlama ve Crystal Reports tümleşik kabuğa dahil edilmez.  
  
#### <a name="2-debugging-support"></a>2. hata ayıklama desteği  
 Tümleşik Kabuk, Visual Studio 'nun topluluk sürümüne dahil olan aynı hata ayıklama altyapısını içerir. Hata ayıklama altyapısı, yönetilen kod için ortak hata ayıklayıcıyı ve ayrıca çalıştırma, ekleme, kesme noktası ayarlama, düzenleme ve devam etme gibi ilgili özellikleri içerir. Ancak, hata ayıklama altyapısı SQL Server veritabanı hata ayıklamasını desteklemez.  
  
 Yerel hata ayıklama desteği temel hata ayıklayıcı paketine dahil edilse de, ek dilleri destekleyecek şekilde genişletemezsiniz.  
  
#### <a name="3-source-code-control-integration"></a>3. kaynak kodu denetimi tümleştirmesi  
 Tümleşik Kabuk, kaynak kodu denetimi (SCC) uygulamak ve MSSCCı tabanlı ortak kaynak denetimi tümleştirme bileşenleri sağlamak için API 'Ler sağlar.  
  
 SCC tümleştirmesi, Visual Studio 'nun Pro Edition 'ın düzenli bir özelliği olmasa da, Tümleşik kabukta SCC tümleştirmesi sunulmaktadır.  
  
#### <a name="4-build-support"></a>4. derleme desteği  
 Tümleşik Kabuk, derleme desteği sağlar. [MSBuild başvurusunda](../msbuild/msbuild-reference.md)derlemeler hakkında bilgi bulabilirsiniz.  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Tümleşik kabuğa dahil edilen özellikler  
 Aşağıda, Tümleşik kabukta bulunmayan özelliklerin bir listesi verilmiştir:  
  
- Sınıf Tasarımcısı  
  
- PreEmptive Protection - Dotfuscator  
  
- Dil özellikleri  
  
- VSHost  
  
- Tümleşik kabuğa Visual Studio dilleri veya ilişkili proje şablonları ya da proje öğesi şablonları dahil değildir. Diğer özelliklerin dile özgü uygulamaları dahil değildir, örneğin Visual Basic kod parçacıkları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio 'Ya genel bakış 'ı genişletme](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
