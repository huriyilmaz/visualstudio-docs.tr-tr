---
title: Web projesi temelleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95c9f7c530d50a7eb89ebe33fad3862f036972d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825621"
---
# <a name="web-project-essentials"></a>Web Projesi Temel Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Web projeleri Web uygulamaları oluşturur. Web projesini, akıllı Web sayfaları olan bir Web uygulaması oluşturmak için kullanabilirsiniz. Akıllı bir Web sayfasında, Web sayfasını istek üzerine işleyen sunucu tarafı kodu vardır.  
  
 Veya gibi geleneksel programlama dillerini kullanarak, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] bir kullanıcıdan bilgi toplamak ve işlemek, bir veritabanında depolamak ve bu şekilde devam etmek Için akıllı Web sayfaları oluşturabilirsiniz.  
  
- Arka plan kod modeli, bağımlı kaynak kodu dosyalarını. aspx veya. asmx uzantılı web sayfalarıyla ilişkilendirir. Örneğin, Hello. aspx bağımlı kaynak kodu dosyası hello.aspx.cs olabilir.  
  
- Akıllı bir Web sayfasıyla ilişkili sunucu tarafı kodu, Web sitesi/bin klasöründe bulunan yürütülebilir bir dosyaya derlenir.  
  
- Belirli bir Web sayfasıyla ilişkilendirilmemiş yardımcı sınıflar gibi ek kaynak kodu dosyaları Web sitesi/App_Code klasöründe bulunur.  
  
  - Web sitesi projesi (WSP) her akıllı Web sayfası için bir yürütülebilir dosya oluşturur. Ek yürütülebilir dosyalar/App_Code klasöründeki herhangi bir kaynak kod dosyasından oluşturulur.  

  - Web uygulaması projesi (WAP), tüm akıllı Web sayfaları için kodu ve/App_Code klasöründeki tüm kaynak dosyaları birleştiren tek bir yürütülebilir dosya oluşturur.  
  
- Web projesinin çözüm dosyası, Web sitesinden ayrı olarak bulunur. Varsayılan olarak, çözüm dosyaları \Documents yolunda ve Settings \\ *YourAccount* \\ *\<Visual Studio ####>* \Documents \projects \\ *yourwebsite*konumundadır.  
  
    > [!NOTE]
    > Çözüm dosyasını Web sitesiyle birlikte tutmak istiyorsanız, dosyayı buraya taşıyın ve yeniden açın.  
  
- Visual Studio 'da çözüm dosyası olmayan bir Web sitesi açarsanız, bu dosya için otomatik olarak yeni bir çözüm dosyası oluşturulur.  
  
- Web projelerinin proje dosyaları yok. Proje bilgileri çözüm dosyasında, web.config dosyasında ve başka bir yerde saklanır.  
  
- Web projesine genel özellikler eklemek, otomatik olarak Web projesi çözüm klasöründe bir depolama dosyası oluşturur.  
  
- Akıllı bir Web sayfası, Page yönergesini veya etiketini kullanarak sunucu tarafı programlama diliyle ilişkilendirilebilir \<script runat="server"> .  
  
- Ayrıca, Web sayfalarında herhangi bir komut dosyası dilinde yazılmış sayıda istemci tarafı betik bloğu bulunabilir.  
  
- Proje ve öğe şablonları ve projeye kayıt eklenerek bir Web sitesi proje sistemi uygulanır [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] .  
  
- WAP sistemi, proje türü olarak da adlandırılan bir proje alt türü olarak uygulanır. [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)]WAP sistemi oluşturmak için proje WAP alt türü tarafından düzlüyor. Proje alt türleri hakkında daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).  
  
- Bir akıllı Web sayfası, HTML 'yi sunucu tarafı programlama diliyle birleştirir. Sunucu tarafı diline, içerilen dil denir. Kapsanan bir dili desteklemek için, Web projesi sisteminin arabirimlerin ailesini uygulaması gerekir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  
  
  - Bir düzenleyicide bulunan dili desteklemek için, HTML dil hizmetinin içerilen dil kodunu içerilen dil hizmetine görüntülemesi gerekir.  

  - Hata işaretçileri (kırmızı dalgalı Glar), her zaman kod düzenleyicisinin birincil arabelleğinde oluşturulmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Projeleri](../../extensibility/internals/web-projects.md)
