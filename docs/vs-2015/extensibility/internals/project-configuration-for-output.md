---
title: Çıkış için proje yapılandırması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: addd7e8630ce35c6bdbbbb4c063197f75a74c97d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300674"
---
# <a name="project-configuration-for-output"></a>Çıkış için Proje Yapılandırması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Her yapılandırma, çalıştırılabilir veya kaynak dosyaları gibi çıkış öğeleri üreten bir yapı işlemi kümesini destekleyebilir. Bu çıkış öğeleri kullanıcıya özeldir ve yürütülebilir dosyalar (. exe,. dll,. lib) ve kaynak dosyaları (. IDL,. h dosyaları) gibi ilgili çıkış türlerini bağlayan gruplara yerleştirilebilir.  
  
 Çıkış öğelerine <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> yöntemler aracılığıyla ulaşılabilir ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> yöntemleriyle Numaralandırılabilir. Çıkış öğelerini gruplandırmak istediğinizde, projeniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> arabirimini de uygulamalıdır.  
  
 `IVsOutputGroup` uygulayarak geliştirilen yapı, projelerin kullanıma göre çıkışları gruplandırmasının olanaklı olmasına olanak sağlar. Örneğin, bir DLL program veritabanı (PDB) ile gruplanmış olabilir.  
  
> [!NOTE]
> PDB dosyası hata ayıklama bilgilerini içerir ve. dll veya. exe derlerken ' hata ayıklama bilgisi oluştur ' seçeneği belirtildiğinde oluşturulur. . Pdb dosyası genellikle yalnızca hata ayıklama proje yapılandırmasında oluşturulur.  
  
 Projenin desteklediği her yapılandırma için aynı sayıda grubu döndürmesi gerekir, ancak bir grup içinde yer alan çıkışların sayısı yapılandırmadan yapılandırmaya farklılık gösterebilir. Örneğin, proje Matt DLL 'SI hata ayıklama yapılandırmasında mattd. dll ve mattd. pdb içerebilir, ancak perakende yapılandırmasına yalnızca Matt. dll dahil edebilir.  
  
 Gruplar, yapılandırmadan bir proje içinde yapılandırmaya kadar kurallı ad, görünen ad ve grup bilgileri gibi aynı tanımlayıcı bilgilerine de sahiptir. Bu tutarlılık, yapılandırma değişse bile dağıtımın ve paketlemeye devam etmesine olanak tanır.  
  
 Gruplar, paketleme kısayollarının anlamlı bir şeyi işaret etmesine izin veren bir anahtar çıkışına da sahip olabilir. Herhangi bir grup belirli bir yapılandırmada boş olabilir, bu nedenle bir grubun boyutuyla ilgili hiçbir varsayımda yapılmalıdır. Herhangi bir yapılandırmadaki her bir grubun boyutu (çıkış sayısı), aynı yapılandırmadaki başka bir grubun boyutundan farklı olabilir. Aynı zamanda başka bir yapılandırmadaki aynı grubun boyutundan farklı olabilir.  
  
 ![Çıkış Grupları grafiği](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Çıkış grupları  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> arabiriminin birincil kullanımı, yönetim nesneleri oluşturma, dağıtma ve hata ayıklama ve projelere çıkışları gruplama özgürlüğü sağlamak için erişim sağlamaktır. Bu arabirimin kullanımı hakkında daha fazla bilgi için bkz. [Proje yapılandırma nesnesi](../../extensibility/internals/project-configuration-object.md).  
  
 Önceki diyagramda, oluşturulan grup, yapılandırmalar arasında (bD. exe veya b. exe) bir anahtar çıkışına sahiptir, böylece Kullanıcı, oluşturulan yapılandırmanın ne olursa olsun kısayol 'un çalıştığını bilmek için bir kısayol oluşturabilir. Grup kaynağında anahtar çıkışı yok, bu nedenle Kullanıcı buna bir kısayol oluşturamaz. Oluşturulan hata ayıklama grubunda anahtar çıkışı varsa, ancak oluşturulan perakende grubu, yanlış bir uygulama olabilir. Daha sonra, herhangi bir yapılandırmanın çıkış içermeyen bir grubu varsa ve sonuç olarak anahtar dosyası yoksa, çıkışları içeren bu gruba sahip diğer yapılandırmaların anahtar dosyaları olamaz. Yükleyici düzenleyiciler kurallı adların ve grupların görünen adlarının yanı sıra bir anahtar dosyasının varlığını kabul eder ve yapılandırmalara bağlı olarak değiştirmeyin.  
  
 Bir projede paketlemek veya dağıtmak istemediğiniz bir `IVsOutputGroup` varsa, bu çıktıyı bir gruba yerleştirmemeye yeterli olduğunu unutmayın. Bu çıktı, gruplandırmadan bağımsız olarak tüm yapılandırma çıkışlarını döndüren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> yöntemi uygulayarak normal olarak yine de listelenebilir.  
  
 Daha fazla bilgi için, [Projeler Için MPF](https://archive.codeplex.com/?p=mpfproj12)konumundaki özel proje örneğindeki `IVsOutputGroup` uygulamasına bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md)   
   [oluşturmak Için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)  
 [Proje yapılandırma nesnesi](../../extensibility/internals/project-configuration-object.md)   
 [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
