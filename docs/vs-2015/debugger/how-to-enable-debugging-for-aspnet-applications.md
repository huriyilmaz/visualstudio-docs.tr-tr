---
title: 'Nasıl yapılır: ASP.NET uygulamaları için hata ayıklamayı etkinleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726e964a0db2fae1b902f54a14e206dbc03a148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477006"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Nasıl Yapılır: ASP.NET Uygulamaları için Hata Ayıklamayı Etkinleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklamayı etkinleştirmek için, bunu **Proje özellikleri** sayfasında ve uygulamanın web.config dosyasında etkinleştirmeniz gerekir.  
  
> [!NOTE]  
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](/previous-versions/zbhkx167(v=vs.140)).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Proje özelliklerinde ASP.NET hata ayıklamayı etkinleştirmek için (Visual Basic / C#)  
  
1. **Çözüm Gezgini**, bir Web projesinin adına sağ tıklayın ve **Özellikler**' i seçin.  
  
2. Proje Özellikleri sayfasında **Web** sekmesine tıklayın.  
  
3. **Hata ayıklayıcıları**altında **ASP.net** onay kutusunu seçin.  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Web.config dosyasında hata ayıklamayı etkinleştirmek için  
  
1. Herhangi standart bir metin düzenleyicisi veya XML ayrıştırıcısını kullanarak web.config dosyasını açın.  
  
    > [!NOTE]  
    > Ancak, bir Web tarayıcısı kullanarak dosyaya uzaktan erişemezsiniz. Güvenlik nedenleriyle, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], Microsoft IIS'i Web.config dosyalarına doğrudan tarayıcı erişimini engellemeye yardımcı olacak şekilde yapılandırır. Bir tarayıcı kullanarak bir yapılandırma dosyasına erişmeye çalışırsanız, HTTP erişim hatası 403 (yasak) alırsınız.  
  
2. Web.config bir XML dosyasıdır ve bu yüzden etiketlerle işaretlenmiş iç içe yerleştirilmiş bölümler içerir. Öğesini bulun `configuration/system.web/compilation` . Derleme ögesi yoksa, onu oluşturun.  
  
3. `compilation` öğesi bir `debug` özniteliği içermiyorsa, özniteliği öğeye ekleyin.  
  
4. `debug` öznitelik değerinin `true`olarak ayarlandığından emin olun.  
  
Web.config dosyası, aşağıdaki örnek gibi görünmelidir. Yapılandırma ve system.web öğeleri arasında bölümler olabileceğini unutmayın  
  
- yapılandırma ve system.web öğeleri arasındaki öğe bölümleri  
  
- system.web ve derleme öğeleri arasındaki öğe bölümleri  
  
- Derleme ögesi, diğer öznitelikleri ve öğeleri içerebilir.  
  
## <a name="example"></a>Örnek  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web.config dosyalarda yapılan değişiklikleri otomatik olarak algılar ve yeni yapılandırma ayarlarını uygular. Değişikliklerin etkili olması için bilgisayarı yeniden başlatmanız veya IIS sunucusunu yeniden başlatmanız gerekmez.  
  
Bir Web sitesi birden çok sanal dizin ve alt dizinler içerebilir ve her birinde Web.config dosyaları bulunabilir. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamalar, URL yolundaki daha yüksek düzeylerdeki Web.config dosyalarından ayarları devralınır. Hiyerarşik yapılandırma dosyaları, aynı anda çeşitli [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamalarının ayarlarını değiştirmenize olanak tanır, örneğin hiyerarşide onun altındaki tüm uygulamalar için. Ancak, `debug`, hiyerarşide daha düşük bir dosyada ayarlanırsa, daha yüksek değeri geçersiz kılar.  
  
Örneğin, `debug="true"` içinde belirtebilirsiniz `www.microsoft.com/aaa/Web.config` ve AAA klasöründeki ya da aaa 'ın herhangi bir alt klasöründeki herhangi bir uygulama bu ayarı devralmasını sağlayacaktır. Bu nedenle, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamanız ' de ise,, vb `www.microsoft.com/aaa/bbb` . gibi bu ayarı devralınır [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] `www.microsoft.com/aaa/ccc` `www.microsoft.com/aaa/ddd` . Tek istisna durum, bu uygulamalardan biri kendi alt Web.config dosyasını kullanarak ayarı geçersiz kılarsa söz konusudur.  
  
Hata ayıklama modunu etkinleştirme, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamanızın performansını önemli ölçüde etkiler. Bir yayınlama uygulaması dağıtmadan veya performans ölçümleri gerçekleştirmeden önce, hata ayıklama modunu devre dışı bırakmayı unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[ASP.NET ve AJAX Uygulamalarında Hata Ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)  
