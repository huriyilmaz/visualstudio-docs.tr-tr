---
title: Genel, hata ayıklama, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c53af4a8e0f42708ab94d7206a9c0cc54819798
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573545"
---
# <a name="general-debugging-options-dialog-box"></a>Genel, Hata Ayıklama, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Araçlar/Seçenekler/hata ayıklama/genel** sayfası aşağıdaki seçenekleri ayarlamanıza olanak sağlar:  
  
 **Tüm kesme noktalarını silmeden önce sor**  
 **Tüm kesme noktalarını Sil** komutu tamamlanmadan önce onay gerektirir.  
  
 **Bir işlem kesildiğinde tüm işlemleri kes**  
 Bir kesme oluştuğunda, hata ayıklayıcının eklendiği tüm süreçler eşzamanlı olarak kesilir.  
  
 **Özel durum AppDomain veya yönetilen/yerel sınırlar olduğunda kes**  
 Yönetilen veya karma mod hata ayıklamada, ortak dil çalışma zamanı, aşağıdaki koşullar doğru olduğunda, uygulama etki alanı sınırları veya yönetilen/yerel sınırları karşılıklı yapan özel durumları yakalayabilir:  
  
 1 \) yerel kod, yönetilen kodu COM birlikte çalışabilirliği kullanarak çağırdığında ve yönetilen kod bir özel durum oluşturduğunda. Bkz. [com birlikte çalışabilirliğine giriş](https://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2 \) uygulama etki alanı 1 ' de çalıştırılan yönetilen kod, uygulama etki alanı 2 ' deki Yönetilen kodu çağırdığında ve uygulama etki alanı 2 ' deki kod bir özel durum oluşturur. Bkz. [uygulama etki alanlarıyla programlama](https://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3 \) kod, yansıma kullanarak bir işlevi çağırdığında ve işlev bir özel durum oluşturduğunda. Bkz. [yansıma](https://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 2\) ve 3), özel durum bazen ortak dil çalışma zamanı yerine `mscorlib` yönetilen kod tarafından yakalanır. Bu seçenek `mscorlib` tarafından yakalanan özel durumların kesilmesini etkilemez.  
  
 **Adres düzeyinde hata ayıklamayı etkinleştir**  
 Adres düzeyinde hata ayıklama için gelişmiş özellikleri ( **ayrıştırılmış** pencere, **Yazmaçları** penceresi ve adres kesme noktaları) sağlar.  
  
 **Kaynak kullanılamıyorsa ayrıştırılmış derlemeyi göster**  
 Kaynak kullanılamayan kodun hatalarını ayıklamanıza çalıştığınızda otomatik olarak **ayrıştırılmış** pencereyi gösterir.  
  
 **Kesme noktası filtrelerini etkinleştir**  
 Yalnızca belirli işlemlerin, iş parçacıklarının veya bilgisayarların etkilenmeleri için kesme noktalarında filtre ayarlamanıza olanak sağlar.  
  
 **Özel durum yardımcısını etkinleştir**  
 Yalnızca yönetilen kod için. Yönetilen özel durumlar özel durum Yardımcısı iletişim kutusunu açar.  Bkz. [özel durum Yardımcısı](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **İşlenmeyen özel durumlarda çağrı yığınını geriye doğru izleme**  
 **Çağrı yığını** penceresinin, işlenmeyen özel durum olmadan önce çağrı yığınını noktaya geri almasına neden olur.  
  
 **Yalnızca kendi kodum etkinleştir**  
 Hata ayıklayıcı yalnızca Kullanıcı kodu ("My Code") içinde görüntülenir ve sistem kodunu ve en iyileştirilmiş veya hata ayıklama sembolleri olmayan diğer kodu yoksayar.  
  
 **Değişkenler penceresinde Kullanıcı olmayan nesneler için tüm üyeleri göster (yalnızca Visual Basic)**  
 Kullanıcı olmayan kodda ("My Code" değil), genel olmayan üyelerin görüntülenmesini etkinleştirir.  
  
 **Başlatmada Kullanıcı kodu yoksa uyar**  
 Hata ayıklama Yalnızca kendi kodum etkinken başlatıldığında, Kullanıcı kodu ("My Code") olmadığında bu seçenek sizi uyarır.  
  
 **.NET Framework kaynak adımlamayı etkinleştir**  
 Hata ayıklayıcının .NET Framework kaynak üzerinde adıma çalışmasına izin verir. Bu seçeneğin etkinleştirilmesi Yalnızca kendi kodum otomatik olarak devre dışı bırakır .NET Framework sembolleri bir önbellek konumuna indirilir. **Seçenekler** iletişim kutusu, **hata ayıklama** kategorisi, **semboller** sayfasında önbellek konumunu değiştirebilirsiniz.  
  
 **Özellikler ve işleçler üzerinde adımla (yalnızca yönetilen)**  
 Hata ayıklayıcının Yönetilen koddaki Özellikler ve işleçlere erişmesini önler.  
  
 **Özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**  
 Değişkenler Windows ve **QuickWatch** iletişim kutusunda özelliklerin ve örtük işlev çağrılarının otomatik değerlendirmesini etkinleştirir.  
  
 **Değişkenler Windows 'daki (C# ve yalnızca JavaScript) nesnelerde dize dönüştürme işlevini çağır**  
 Değişkenler penceresinde nesneleri değerlendirirken örtük bir dize dönüştürme çağrısı yürütür. Bu nedenle, bu sonuç tür adı yerine bir dize olarak görüntülenir. Yalnızca C# kodda hata ayıklanırken geçerlidir. Bu ayar DebuggerDisplay özniteliği tarafından geçersiz kılınabilir (bkz. [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Kaynak sunucu desteğini etkinleştir**  
 Visual Studio hata ayıklayıcısına SrcSrv (`srcsrv.dll`) protokolünü uygulayan kaynak sunuculardan kaynak dosyaları almasını söyler. Team Foundation Server ve Windows için hata ayıklama araçları, protokolü uygulayan iki kaynak sunucularıdır. SrcSrv kurulumu hakkında daha fazla bilgi için bkz. Windows için hata ayıklama araçları belgeleri. Ayrıca bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> . Pdb dosyalarını okuma dosyalarında rastgele kod yürütebildiğinden, sunucuya güvendiğinizden emin olun.  
  
 **Kaynak sunucu tanılama iletilerini çıkış penceresine Yazdır**  
 Kaynak sunucu desteği etkinleştirildiğinde, bu ayar tanılama görüntüsünü etkinleştirir.  
  
 **Kısmi güven derlemeleri (yalnızca yönetilen) için kaynak sunucuya izin ver**  
 Kaynak sunucu desteği etkinleştirildiğinde, bu ayar kısmi güven derlemeleri için kaynak almamanın varsayılan davranışını geçersiz kılar.  
  
 **Kesme noktaları ve geçerli ifade için tüm satırı Vurgula**  
 Hata ayıklayıcı bir kesme noktasını veya geçerli ifadeyi vurgualdığında, tüm satırı vurgular.  
  
 **Kaynak dosyaların özgün sürümle tam olarak eşleşmesini gerektir**  
 Hata ayıklayıcıya bir kaynak dosyanın, hata ayıklaması yaptığınız yürütülebilir dosyayı oluşturmak için kullanılan kaynak kodun sürümüyle eşleştiğini doğrulamasını söyler. Sürüm eşleşmezse, eşleşen bir kaynak bulmanız istenir. Eşleşen bir kaynak bulunamazsa, hata ayıklama sırasında kaynak kodu gösterilmez.  
  
 **Tüm çıkış penceresi metnini komut penceresine yeniden yönlendir**  
 Genellikle **Çıkış** penceresinde görüntülenen tüm hata ayıklayıcı iletilerini **hemen** bir pencereye gönderir.  
  
 **Değişkenler penceresinde nesnelerin ham yapısını göster**  
 Tüm nesne yapısı görünümü özelleştirmelerini kapatır. Özelleştirmeleri görüntüle hakkında daha fazla bilgi için bkz. [yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-managed-objects.md).  
  
 **Modül yüklemesinde JıT iyileştirmesini bastır (yalnızca yönetilen)**  
 Modül yüklendiğinde yönetilen kodun JıT iyileştirmesini devre dışı bırakır ve hata ayıklayıcı eklendiğinde JıT derlenir. İyileştirmenin devre dışı bırakılması, performans masrafına karşın bazı sorunların hatalarını ayıklamanızı kolaylaştırabilir. Yalnızca kendi kodum kullanıyorsanız, JıT iyileştirmesini gizleme Kullanıcı dışı kodun kullanıcı kodu ("My Code") olarak görünmesine neden olabilir.  
  
 **Başlatma üzerinde hiçbir sembol yoksa uyar (yalnızca yerel)**  
 Hata ayıklayıcının simge bilgilerine sahip olmadığı bir programda hata ayıklamaya çalıştığınızda bir uyarı iletişim kutusu görüntüler.  
  
 **Başlatma sırasında betik hata ayıklaması devre dışıysa uyar**  
 Hata ayıklayıcı komut dosyası hata ayıklama devre dışıyken başlatıldığında bir uyarı iletişim kutusu görüntüler.  
  
 **DLL dışarı aktarmaları yükle**  
 DLL dışarı aktarma tablolarını yükler. DLL dışarı aktarma tablolarından sembol bilgileri, Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri veya sıralama ya da sembolleri olmayan herhangi bir dll ile çalışıyorsanız yararlı olabilir. Dll dışa aktarma bilgilerini okuma bazı ek yük içerir. Bu nedenle, bu özellik varsayılan olarak kapalıdır.  
  
 Dll 'nin dışarı aktarma tablosunda hangi simgelerin kullanılabildiğini görmek için `dumpbin /exports` kullanın. Semboller, 32 bit sistem dll 'si için kullanılabilir. @No__t_0 çıktısını okuyarak, alfasayısal olmayan karakterler de dahil olmak üzere tam işlev adını görebilirsiniz. Bu, bir işlev bir kesme noktası ayarlamak için yararlıdır. DLL dışarı aktarma tablolarındaki işlev adları, hata ayıklayıcının başka bir yerinde kesilmiş görünebilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. Daha fazla bilgi için bkz. [döküm bin/dışarı aktarmalar](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Paralel Yığınlar diyagramını aşağıdan yukarı göster**  
 Yığınların **Paralel Yığınlar** penceresinde Görüntülenme yönünü denetler.  
  
 **Yazılan veriler değeri değiştirmediyse GPU bellek erişimi özel durumlarını yoksay**  
 Veriler değişmediyse hata ayıklama sırasında algılanan yarış durumlarını yoksayar. Daha fazla bilgi için bkz. [GPU kodunda hata ayıklama](../debugger/debugging-gpu-code.md).  
  
 **Yönetilen Uyumluluk modunu kullan**  
 Bu senaryoları etkinleştirmek için varsayılan hata ayıklama altyapısını eski bir sürümle değiştirir:  
  
- C#, Vb veya F# dışında bir .NET Framework dili kullanıyorsunuz (Bu,/CLI içerir C++).  
  
- Karışık mod hata ayıklaması yaparken projeler için C++ Düzenle ve devam et özelliğini etkinleştirmek istiyorsunuz.  
  
  Yönetilen Uyumluluk modunun seçilmesi, yalnızca varsayılan hata ayıklama altyapısında uygulanan bazı özellikleri devre dışı bıraktığını unutmayın.  
  
  **Yerel uyumluluk modunu kullan**  
  Bu seçenek belirlendiğinde, hata ayıklayıcı yeni yerel hata ayıklayıcı yerine Visual Studio 2010 yerel hata ayıklayıcısını kullanır.  
  
  Yeni hata ayıklama altyapısı .NET C++ C++ ifadeleri değerlendirmeyi desteklemediğinden, .net Code hata ayıklaması yaparken bu seçeneği kullanmanız gerekir. Ancak, yerel uyumluluk modunu etkinleştirmek, geçerli hata ayıklayıcı uygulamasına bağımlı birçok özelliği çalışır şekilde devre dışı bırakır. Örneğin, eski altyapıda Visual Studio 2015 projelerinde `std::string` gibi yerleşik türler için birçok Görselleştiriciler yoktur.  Bu durumlarda en iyi hata ayıklama deneyimi için Visual Studio 2013 projelerini kullanın.  
  
  **Eski C# ve vb ifadesini kullanın değerlendiricileri**  
  Hata ayıklayıcı, Visual Studio 2015 C#Roslyn tabanlı ifade değerlendiricileri yerine Visual Studio 2013/vb Expression değerlendiricileri kullanır.  
  
  **Güvenli olmayan işlemlere karşı özel hata ayıklama görselleştiricileri kullanıldığında uyar (yalnızca yönetilen)**  
  Hata ayıklanan işlemde kod çalıştıran özel bir hata ayıklayıcı görselleştiricisi kullandığınızda, güvenli olmayan kod çalıştırdığından, Visual Studio sizi uyarır.  
  
  **Windows hata ayıklama yığın ayırıcısını etkinleştir (yalnızca yerel)**  
  Yığın tanılamayı geliştirmek için Windows hata ayıklama yığını 'nı sağlar. Bu seçeneğin etkinleştirilmesi, hata ayıklama performansını etkiler.  
  
  **XAML için Kullanıcı arabirimi hata ayıklama araçlarını etkinleştir**  
  Canlı görsel ağaç ve canlı özelliği, hata ayıklamayı başlattığınızda (F5) desteklenen bir proje türü olarak görüntülenir. Daha fazla bilgi için bkz. [hata ayıklama SıRASıNDA xaml özelliklerini inceleme](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Canlı görsel ağaçta seçili öğeleri önizleyin**  
  Bağlamı seçili olan XAML öğesi, **canlı görsel ağaç** penceresinde de seçilidir.  
  
  **Çalışma zamanı araçlarını uygulamada göster**  
  Hata ayıklamakta olan XAML uygulamasının ana penceresindeki bir araç çubuğunda **canlı görsel ağaç** komutlarını gösterir. Bu seçenek, Visual Studio 2015 güncelleştirme 2 ' de sunulmuştur.  
  
  **Hata ayıklarken Tanılama Araçları etkinleştir**  
  Hata ayıklarken **Tanılama araçları** pencere görüntülenir. Daha fazla bilgi için bkz. [hata ayıklayıcı ile tümleşik profil oluşturma](/visualstudio/profiling/running-profiling-tools-with-or-without-the-debugger).  
  
  **Hata ayıklama sırasında Perftıp geçen süreyi göster**  
  Kod penceresi, hata ayıklarken belirli bir yöntem çağrısının geçen süresini görüntüler.  
  
  **Düzenle ve devam et 'i etkinleştir**  
  Hata ayıklarken Düzenle ve devam et işlevini kullanabilirsiniz.  
  
  **Yerel Düzenle ve devam et 'i etkinleştir**  
  Yerel C++ kodda hata ayıklarken Düzenle ve devam et işlevini kullanabilirsiniz. Daha fazla bilgi için bkz. [Düzenle ve devam et C++(görsel)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Değişiklikleri devam ederken Uygula (yalnızca yerel)**  
  Visual Studio, işleme bir kesme durumundan devam ederken yaptığınız bekleyen kod değişikliklerini otomatik olarak derler ve uygular. Seçili değilse, hata ayıkla menüsündeki "kod değişikliklerini Uygula" öğesini kullanarak değişiklikleri uygulamayı seçebilirsiniz.  
  
  **Eski kod hakkında uyar (yalnızca yerel)**  
  Eski kod hakkında uyarı alın.  
  
  **Önceden derlemeye izin ver (yalnızca yerel)**  
  Önceden derlemeye izin veriliyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)
