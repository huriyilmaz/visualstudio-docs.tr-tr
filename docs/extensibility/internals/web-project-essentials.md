---
title: Web Project Essentials | Microsoft Docs
description: Web projelerinin şirket içinde nasıl çalışmalarına ilişkin iç ayrıntıları Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 54888223ec789babd4af15c6b675a138bdb81520
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724985"
---
# <a name="web-project-essentials"></a>Web Projesi Temel Bileşenleri
Web projeleri Web uygulamaları oluşturun. Akıllı Web sayfalarına sahip bir Web uygulaması oluşturmak için bir Web projesi kullanabilirsiniz. Akıllı Bir Web sayfasında, Web sayfasını isteğe bağlı olarak işleyici sunucu tarafı kodu vardır.

 veya gibi geleneksel programlama dillerini kullanarak, bir kullanıcıdan bilgi toplamak ve işlemek, bunu bir veritabanında depolamak ve bu gibi işlemleri yapmak için akıllı [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Web sayfaları oluşturabilirsiniz.

- Arka alınan kod modeli, bağımlı kaynak kod dosyalarını .aspx veya .asmx dosya uzantısına sahip Web sayfalarıyla ilişkilendirır. Örneğin, hello.aspx hello.aspx.cs bağımlı kaynak kod dosyasına sahip olabilir.

- Bir akıllı Web sayfasıyla ilişkili sunucu tarafı kodu, Web sitesi /bin klasöründe bulunan yürütülebilir bir dosyaya derlenmiş.

- Belirli bir Web sayfasıyla ilişkilendirilen yardımcı sınıflar gibi ek kaynak kodu dosyaları Web sitesi /App_Code klasöründe bulunur.

  - Web sitesi projesi (WSP), her akıllı Web sayfası için bir yürütülebilir dosya üretir. /App_Code klasöründeki tüm kaynak kod dosyalarından ek yürütülebilir dosyalar oluşturulur.

  - Web uygulaması projesi (WAP), tüm akıllı Web sayfalarının kodunu ve /App_Code klasöründeki tüm kaynak dosyaları birleştiren tek bir yürütülebilir dosya oluşturur.

- Bir Web projesinin çözüm dosyası, Web sitesinden ayrı olarak bulunur. Varsayılan olarak, çözüm dosyaları \Documents konumunda bulunur ve \\ *YourAccount*\My Documents \\ *\<Visual Studio ####>* \Projects \\ *YourWebSite* dizininde Ayarlar.

  > [!NOTE]
  > Çözüm dosyasını Web sitesinde tutmak için buraya taşımanız ve yeniden açmanız gerekir.

- Bir web sitesinde çözüm dosyası Visual Studio bir Web sitesi açarsanız, bu site için otomatik olarak yeni bir çözüm dosyası oluşturulur.

- Web projelerinin proje dosyası yoktur. Project bilgileri çözüm dosyasında, web.config başka bir yerde depolanır.

- Web projesine genel özellikler eklemek, Web projesi çözüm klasöründe otomatik olarak bir depolama dosyası oluşturur.

- Akıllı Web sayfası, Page yönergesi veya etiketi kullanılarak sunucu tarafı programlama diliyle \<script runat="server"> ilişkilendirilebilirsiniz.

- Ayrıca, Web sayfaları herhangi bir betik dilinde yazılmış herhangi bir sayıda istemci tarafı betik bloğuna sahip olabilir.

- Bir Web sitesi proje sistemi, proje ve öğe şablonları eklip projeye kayıt [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] uygulanarak uygulanır.

- WAP sistemi, proje türü olarak da adlandırılan bir proje alt türü olarak uygulanır. Proje, [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] WAP sistemi oluşturmak için WAP alt türü tarafından 100'e sahiptir. Proje alt türleri hakkında daha fazla bilgi için [bkz. Project Alt Türleri.](../../extensibility/internals/project-subtypes.md)

- Akıllı Web sayfası, HTML'yi sunucu tarafı programlama diliyle birleştirir. Sunucu tarafı dili, içerdiği dil olarak adlandırılan dildir. Bir içerdiği dili desteklemek için Web proje sisteminin arabirim ailesini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> uygulaması gerekir.

  - Bir düzenleyicide bulunan dili desteklemek için HTML dil hizmetinin, içerdiği dil kodunu görüntülemeyi, içerdiği dil hizmetine ertelemesi gerekir.

  - Kod düzenleyicisinin birincil arabelleğinde her zaman hata işaretçileri (kırmızı çizgi) oluşturularak oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Projeleri](../../extensibility/internals/web-projects.md)
