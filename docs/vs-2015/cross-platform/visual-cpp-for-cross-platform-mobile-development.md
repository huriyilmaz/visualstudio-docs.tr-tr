---
title: Çoklu Platform Mobil Uygulama Geliştirme için Visual C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e947800c82036b061b2f48303733690a95ec53bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573072"
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Çoklu Platform Mobil Uygulama Geliştirme için Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İOS, Android ve Windows cihazları için yerel C++ uygulamaları oluşturabilir ve Çoklu Platform Mobil Uygulama Geliştirme için Visual C++ kullanarak iOS, Android ve Windows için oluşturulan kitaplıklarda ortak kodu paylaşabilirsiniz. Bu, Visual Studio 2015 ' de bulunan ve paylaşılan kitaplıkların ve yerel uygulamaların platformlar arası geliştirmesi için ihtiyaç duyduğunuz SDK 'Ları ve araçları yükleyen bir seçenektir. Yüklendiğinde, Windows, Windows Phone ve Xbox 'a ek olarak iOS ve Android cihazlarda ve platformlarında çalışan kodu oluşturmak için Visual C++ kullanabilirsiniz.  
  
 Birden çok platform için kod yazmak sinir bozucu olabilir. İOS, Android ve Windows için birincil geliştirme dilleri ve araçları her platformda farklıdır. Ancak, tüm platformlar C++ ' da kod yazmayı destekler. Bu, platformlar arasında çekirdek kod yeniden kullanımını etkinleştirmek için kullanabileceğiniz ortak paydadır. C++ dilinde yazılan yerel kod, ters mühendislik için hem daha fazla performansı hem de dayanıklı olabilir. Kod yeniden kullanımı, birden çok platform için uygulama oluştururken hem zaman hem de efor tasarrufu sağlayabilir.  
  
 Çoklu Platform Mobil Uygulama Geliştirme için Visual C++ kullanarak geliştirme birkaç avantaj sunar:  
  
1. **Kolay yükleme.** Visual Studio yükleyicisi, Android ve iOS için uygulamalar veya kitaplıklar oluşturmak için gereken gerekli üçüncü taraf araçları ve SDK 'Ları alır ve kurar. Yapılandırma ve kurulum basit ve genellikle otomatiktir.  
  
2. **Güçlü ve tanıdık bir yapı ortamı.** Visual Studio şablonlarıyla kolayca paylaşılabilir platformlar arası çözümler ve projeler oluşturun. Tek bir ortak arabirim kullanarak tüm projelerin özelliklerini yönetin. Visual Studio düzenleyicisinde tüm kodunuzu düzenleyin ve kod tamamlama ve hata vurgulama için yerleşik platformlar arası IntelliSense 'den yararlanın.  
  
3. **Birleşik bir hata ayıklama deneyimi.** Android cihazlar ve Öykünücüler, iOS simülatörleri ve cihazlar, Windows veya Windows Phone cihazlar ve Öykünücüler dahil olmak üzere tüm platformlarda C++ kodunu izlemek ve adım adım ilerlemek için Visual Studio 'daki birinci sınıf hata ayıklama araçlarını kullanın.  
  
## <a name="get-the-tools"></a>Araçları edinme  
 Çoklu Platform Mobil Uygulama Geliştirme için Visual C++, Visual Studio 2015 ile birlikte gelen yüklenebilir bir seçenektir. Önkoşullar ve yükleme yönergeleri için bkz. [yükleme çoklu platform mobil uygulama geliştirme için Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). İOS için kod oluşturmak üzere bir Mac bilgisayar ve bir Apple iOS Geliştirici hesabı da gerekir. Daha fazla bilgi için bkz. [iOS kullanarak derlemek Için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>En hızlı şekilde katılın  
 Android veya iOS Geliştirme işleminden geliyorsa, kullanmaya başlama hakkında harika bir malzememiz vardır. Visual Studio, ifade ve uyumlu bir geliştirme ortamıdır. Nasıl kullanacağınızı öğrenmek için, [Android geliştiricilere](https://msdn.microsoft.com/library/windows/apps/dn275875.aspx) Başlarken veya [iOS geliştiricileri için](https://msdn.microsoft.com/library/windows/apps/xaml/jj657966.aspx)Başlarken ' i kullanmayı deneyin. Bu konularda, Visual Studio ve Windows ve Windows Phone için platformlar arası uygulamalar geliştirmeniz için gereken kavramlar sunulacaktır. İOS ve Android için ilk platformlar arası uygulamanızı yazmaya başlamak için bkz. [Android ve iOS üzerinde OpenGL ES uygulaması oluşturma](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Çoklu Platform Mobil Uygulama Geliştirme için Visual C++, uygulamalarınıza başlamanıza yardımcı olacak çeşitli şablonlar içerir:  
  
- OpenGLES 2 uygulaması (Android, iOS, Windows Evrensel)  
  
     Paylaşılan bir C++ kod kitaplığı ile birlikte bir Android yerel etkinlik uygulaması, bir iOS uygulaması ve Evrensel Windows uygulaması oluşturmak için bir proje kümesi içeren bir çözüm oluşturur. Bu uygulamalar, her uygulamada aynı dönen kübü çizmek için ortak C++ OpenGL ES kodu kullanılarak oluşturulan platforma özel kitaplıkları kullanır. Bu şablonu kullanmak için Visual Studio 'Yu yüklerken Evrensel Windows uygulaması geliştirme araçları seçeneğini dahil etmeniz gerekir.  
  
- Native-Activity uygulaması (Android)  
  
     Android yerel etkinlik projesi olarak tamamen C++ OpenGL uygulaması oluşturur.  
  
- OpenGLES uygulaması (Android, iOS)  
  
     Hem Android yerel etkinlik uygulaması hem de bir iOS uygulaması oluşturmak için bir proje kümesiyle bir çözüm oluşturur. Bu uygulamalar, her uygulamada aynı dönen kübü çizmek için ortak C++ OpenGL ES kodu kullanılarak oluşturulan platforma özel kitaplıkları kullanır.  
  
- Paylaşılan kitaplık (Android, iOS)  
  
     Paylaşılan bir projede ortak C++ kodunu kullanarak Android dinamik kitaplığı (. so) dosyası ve bir iOS statik kitaplık (. a) dosyası oluşturmak için projelerle bir çözüm oluşturur.  
  
- Temel uygulama (Android, Ant)  
  
     Yalnızca Java kaynak kodu ve Ant derleme sistemi kullanan bir Android "Hello, World" uygulama projesi oluşturur.  
  
- Temel uygulama (Android, Gradle)  
  
     Yalnızca Java kaynak kodu ve Gradle yapı sistemi kullanan bir Android "Hello, World" uygulama projesi oluşturur.  
  
- Temel kitaplık (Android, Ant)  
  
     Yalnızca Java kaynak kodu ve Ant derleme sistemi kullanan bir Android "Hello, World" kitaplık projesi oluşturur.  
  
- Temel kitaplık (Android, Gradle)  
  
     Yalnızca Java kaynak kodu ve Gradle yapı sistemi kullanan bir Android "Hello, World" kitaplık projesi oluşturur.  
  
- Dinamik Paylaşılan kitaplık (Android)  
  
     C++ kodunu kullanarak bir Android dinamik kitaplığı (. so) dosyası oluşturur.  
  
- OpenGLES 2 uygulaması (iOS)  
  
     OpenGL ES 2 iOS uygulaması oluşturmak için bir proje kümesiyle bir çözüm oluşturur. Uygulama, bir iOS uygulamasında dönen kübü çizmek için bir C++ OpenGL ES kodu kitaplığı kullanır. Bu uygulama, C++ kitaplıklarının iOS uygulamanıza nasıl içeri aktarılacağını görmek için iyi bir başlangıç noktasıdır.  
  
- Statik kitaplık (Android)  
  
     Android için statik kitaplık oluşturmak üzere bir proje oluşturur. Bir Android uygulamasında yalnızca bir dinamik kitaplık bağlayabilirsiniz, ancak istediğiniz sayıda statik kitaplığı bağlayabilirsiniz.  
  
- Statik kitaplık (iOS)  
  
     İOS için statik kitaplık oluşturmak üzere bir proje oluşturur.  
  
- Makefile projesi (Android)  
  
     Kendi Android derleme görevleri dosyası projeleriniz için bir proje sarmalayıcısı oluşturur.  
  
## <a name="try-out-sample-code"></a>Örnek kodu deneyin  
 Windows, Android ve iOS uygulamalarında kullanabileceğiniz paylaşılan kod kitaplıklarının nasıl oluşturulacağını ve Android için tamamen yerel etkinlik uygulamaları oluşturmayı gösteren örnekleri indirin. Başlamak için bkz. [platformlar arası mobil geliştirme örnekleri](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>Bu bölümde  
  
1. [Çoklu Platform Mobil Uygulama Geliştirme için Visual C++’ı yükleme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2. [İOS kullanarak derlemek için Araçlar yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3. [Android yerel etkinlik uygulaması oluşturma](../cross-platform/create-an-android-native-activity-app.md)  
  
4. [Android ve iOS üzerinde OpenGL ES uygulaması oluşturma](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5. [Platformlar arası mobil geliştirme örnekleri](../cross-platform/cross-platform-mobile-development-examples.md)
