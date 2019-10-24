---
title: Web projesi temelleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f3d3069d8cc539deeda7c9d44f8d1cbf27e8821
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721670"
---
# <a name="web-project-essentials"></a>Web Projesi Temel Bileşenleri
Web projeleri Web uygulamaları oluşturur. Web projesini, akıllı Web sayfaları olan bir Web uygulaması oluşturmak için kullanabilirsiniz. Akıllı bir Web sayfasında, Web sayfasını istek üzerine işleyen sunucu tarafı kodu vardır.

 @No__t_0 veya [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] gibi geleneksel programlama dillerini kullanarak, bir kullanıcıdan bilgi toplamak ve işlemek, bir veritabanında depolamak ve bu şekilde devam etmek için akıllı Web sayfaları oluşturabilirsiniz.

- Arka plan kod modeli, bağımlı kaynak kodu dosyalarını. aspx veya. asmx uzantılı web sayfalarıyla ilişkilendirir. Örneğin, Hello. aspx bağımlı kaynak kodu dosyası hello.aspx.cs olabilir.

- Akıllı bir Web sayfasıyla ilişkili sunucu tarafı kodu, Web sitesi/bin klasöründe bulunan yürütülebilir bir dosyaya derlenir.

- Belirli bir Web sayfasıyla ilişkilendirilmemiş yardımcı sınıflar gibi ek kaynak kodu dosyaları, Web sitesi/App_Code klasöründe bulunur.

  - Web sitesi projesi (WSP) her akıllı Web sayfası için bir yürütülebilir dosya oluşturur. Ek yürütülebilir dosyalar,/App_Code klasöründeki herhangi bir kaynak kod dosyasından oluşturulur.

  - Web uygulaması projesi (WAP), tüm akıllı Web sayfaları için kodu ve/App_Code klasöründeki tüm kaynak dosyalarını birleştiren tek bir yürütülebilir dosya oluşturur.

- Web projesinin çözüm dosyası, Web sitesinden ayrı olarak bulunur. Varsayılan olarak, çözüm dosyaları \Documents ve Settings '*de \\* \belgelerim \\ *\<Visual Studio # # # # >* \projects \\*etkiweb sitesinden*bulunur.

  > [!NOTE]
  > Çözüm dosyasını Web sitesiyle birlikte tutmak istiyorsanız, dosyayı buraya taşıyın ve yeniden açın.

- Visual Studio 'da çözüm dosyası olmayan bir Web sitesi açarsanız, bu dosya için otomatik olarak yeni bir çözüm dosyası oluşturulur.

- Web projelerinin proje dosyaları yok. Proje bilgileri çözüm dosyasında, Web. config dosyasında ve başka bir yerde saklanır.

- Web projesine genel özellikler eklemek, otomatik olarak Web projesi çözüm klasöründe bir depolama dosyası oluşturur.

- Akıllı bir Web sayfası, Page yönergesini veya \<script runat = "Server" > etiketini kullanarak sunucu tarafı programlama diliyle ilişkilendirilebilir.

- Ayrıca, Web sayfalarında herhangi bir komut dosyası dilinde yazılmış sayıda istemci tarafı betik bloğu bulunabilir.

- Bir Web sitesi proje sistemi, [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projesine proje ve öğe şablonları ve kayıt eklenerek uygulanır.

- WAP sistemi, proje türü olarak da adlandırılan bir proje alt türü olarak uygulanır. WAP sistemini oluşturmak için [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projesi WAP alt türü tarafından düzlüyor. Proje alt türleri hakkında daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).

- Bir akıllı Web sayfası, HTML 'yi sunucu tarafı programlama diliyle birleştirir. Sunucu tarafı diline, içerilen dil denir. Kapsanan bir dili desteklemek için, Web projesi sisteminin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimlerini uygulaması gerekir.

  - Bir düzenleyicide bulunan dili desteklemek için, HTML dil hizmetinin içerilen dil kodunu içerilen dil hizmetine görüntülemesi gerekir.

  - Hata işaretçileri (kırmızı dalgalı Glar), her zaman kod düzenleyicisinin birincil arabelleğinde oluşturulmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Projeleri](../../extensibility/internals/web-projects.md)