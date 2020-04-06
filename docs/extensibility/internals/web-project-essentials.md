---
title: Web Projesi Essentials | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703546"
---
# <a name="web-project-essentials"></a>Web Projesi Temel Bileşenleri
Web projeleri Web uygulamaları oluşturur. Akıllı Web sayfaları olan bir Web uygulaması oluşturmak için bir Web projesini kullanabilirsiniz. Akıllı Web sayfasında, Web sayfasını isteğe bağlı hale getiren sunucu tarafı kodu vardır.

 Bir kullanıcıdan bilgi toplamak [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]ve işlemek, veritabanında depolamak ve benzeri için akıllı Web sayfaları oluşturabilir ve bunlar gibi geleneksel programlama dillerini kullanarak.

- Kod arkası modeli, bağımlı kaynak kod dosyalarını dosya uzantısı .aspx veya .asmx olan Web sayfalarıyla ilişkilendirer. Örneğin, hello.aspx bağımlı kaynak kodu dosyası hello.aspx.cs olabilir.

- Akıllı Bir Web sayfasıyla ilişkili sunucu tarafı kodu, Web sitesi /bin klasöründe bulunan yürütülebilir bir dosyada derlenir.

- Belirli bir Web sayfasıyla ilişkili olmayan yardımcı sınıflar gibi ek kaynak kod dosyaları Web sitesi /App_Code klasöründe bulunur.

  - Bir Web sitesi projesi (WSP), her akıllı Web sayfası için bir yürütülebilir dosya oluşturur. /App_Code klasöründeki herhangi bir kaynak kodu dosyasından ek yürütülebilir dosyalar oluşturulur.

  - Bir Web uygulama projesi (WAP), tüm akıllı Web sayfalarının ve /App_Code klasöründeki tüm kaynak dosyaların kodunu birleştiren tek bir yürütülebilir dosya üretir.

- Bir Web projesinin çözüm dosyası, Web sitesinin kendisinden ayrı olarak bulunur. Varsayılan olarak, çözüm dosyaları \Belgeler ve\\Ayarlar*YourAccount*\My Documents\\*\<Visual Studio ####>* \Projects\\*YourWebSite*adresinde bulunur.

  > [!NOTE]
  > Çözüm dosyasını Web sitesinde tutmak istiyorsanız, dosyayı oraya taşıyın ve yeniden açın.

- Visual Studio'da çözüm dosyası olmayan bir Web sitesini açarsanız, bunun için otomatik olarak yeni bir çözüm dosyası oluşturulur.

- Web projelerinde proje dosyası yoktur. Proje bilgileri çözüm dosyasında, web.config dosyasında ve başka yerlerde depolanır.

- Bir Web projesine genel özellikler eklemek, Web projesi çözüm klasöründe otomatik olarak bir depolama dosyası oluşturur.

- Akıllı bir Web sayfası, Sayfa yönergesi veya \<komut dosyası runat="server"> etiketi kullanılarak sunucu tarafı programlama diliyle ilişkilendirilebilir.

- Ayrıca, Web sayfalarında herhangi bir komut dosyası dilinde yazılmış istemci tarafı komut dosyası blokları herhangi bir sayıda olabilir.

- Proje ve madde şablonları ve [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projeye kayıt eklenerek bir Web sitesi proje sistemi uygulanır.

- Bir WAP sistemi, proje lezzeti olarak da adlandırılan bir proje alt türü olarak uygulanır. Proje [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] WAP sistemi oluşturmak için WAP alt türü ile tatlandırılmıştır. Proje alt türleri hakkında daha fazla bilgi için [Bkz. Proje Alt Türleri.](../../extensibility/internals/project-subtypes.md)

- Akıllı Web sayfası HTML'yi sunucu tarafındaki programlama diliyle birleştirir. Sunucu tarafındaki dil, içerdiği dil olarak adlandırılır. İçerdiği bir dili desteklemek için Web <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> proje sisteminin arabirim ailesini uygulaması gerekir.

  - Bir düzenleyicide bulunan dili desteklemek için HTML dil hizmetinin içerdiği dil kodunu içeren bir dil hizmetine ertelemesi gerekir.

  - Hata işaretçileri (kırmızı squigglies) her zaman kod düzenleyicisinin birincil arabelleği oluşturulmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Projeleri](../../extensibility/internals/web-projects.md)
