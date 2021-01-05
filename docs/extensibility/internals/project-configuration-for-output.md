---
title: Çıkış için proje yapılandırması | Microsoft Docs
description: Her yapılandırmanın destekleyebileceği derleme işlemi ve çıkış öğelerinin kullanılabilir duruma getirilme arabirimlerini ve yöntemlerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe5cb6477808f892b8d36aa5fd616a5a0ea7969
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876330"
---
# <a name="project-configuration-for-output"></a>Çıkış için Proje Yapılandırması
Her yapılandırma, çalıştırılabilir veya kaynak dosyaları gibi çıkış öğeleri üreten bir yapı işlemi kümesini destekleyebilir. Bu çıkış öğeleri kullanıcıya özeldir ve yürütülebilir dosyalar (. exe,. dll,. lib) ve kaynak dosyaları (. IDL,. h dosyaları) gibi ilgili çıkış türlerini bağlayan gruplara yerleştirilebilir.

 Çıkış öğeleri yöntemler aracılığıyla kullanılabilir hale getirilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> ve yöntemlerle numaralandırılabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> . Çıkış öğelerini gruplandırmak istediğinizde, projeniz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> arabirimini uygulamalıdır.

 Uygulaması tarafından geliştirilen yapı, `IVsOutputGroup` projelerin kullanıma göre çıkışları gruplandırmasının olanaklı olmasına olanak sağlar. Örneğin, bir DLL program veritabanı (PDB) ile gruplanmış olabilir.

> [!NOTE]
> PDB dosyası hata ayıklama bilgilerini içerir ve. dll veya. exe derlerken ' hata ayıklama bilgisi oluştur ' seçeneği belirtildiğinde oluşturulur. . Pdb dosyası genellikle yalnızca hata ayıklama proje yapılandırmasında oluşturulur.

 Projenin desteklediği her yapılandırma için aynı sayıda grubu döndürmesi gerekir, ancak bir grup içinde yer alan çıkışların sayısı yapılandırmadan yapılandırmaya farklılık gösterebilir. Örneğin, proje Matt DLL 'SI hata ayıklama yapılandırmasında mattd.dll ve mattd. pdb içerebilir, ancak yalnızca perakende yapılandırmasına matt.dll dahil edebilir.

 Gruplar, yapılandırmadan bir proje içinde yapılandırmaya kadar kurallı ad, görünen ad ve grup bilgileri gibi aynı tanımlayıcı bilgilerine de sahiptir. Bu tutarlılık, yapılandırma değişse bile dağıtımın ve paketlemeye devam etmesine olanak tanır.

 Gruplar, paketleme kısayollarının anlamlı bir şeyi işaret etmesine izin veren bir anahtar çıkışına da sahip olabilir. Herhangi bir grup belirli bir yapılandırmada boş olabilir, bu nedenle bir grubun boyutuyla ilgili hiçbir varsayımda yapılmalıdır. Herhangi bir yapılandırmadaki her bir grubun boyutu (çıkış sayısı), aynı yapılandırmadaki başka bir grubun boyutundan farklı olabilir. Aynı zamanda başka bir yapılandırmadaki aynı grubun boyutundan farklı olabilir.

 ![Çıkış Grupları grafiği](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Çıkış grupları

 Arabirimin birincil kullanımı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> , yönetim nesnelerini oluşturmak, dağıtmak ve hata ayıklamak için erişim sağlamaktır ve projelere çıkışları gruplama özgürlüğü sağlar. Bu arabirimin kullanımı hakkında daha fazla bilgi için bkz. [Proje yapılandırma nesnesi](../../extensibility/internals/project-configuration-object.md).

 Önceki diyagramda, bir grup, yapılandırmalar arasında (bD.exe veya b.exe) bir anahtar çıkışına sahiptir, böylece Kullanıcı oluşturulan yapılandırma ne olursa olsun kısayolun çalıştığını bilip çalışmadığını bilir. Grup kaynağında anahtar çıkışı yok, bu nedenle Kullanıcı buna bir kısayol oluşturamaz. Oluşturulan hata ayıklama grubunda anahtar çıkışı varsa, ancak oluşturulan perakende grubu, yanlış bir uygulama olabilir. Daha sonra, herhangi bir yapılandırmanın çıkış içermeyen bir grubu varsa ve sonuç olarak anahtar dosyası yoksa, çıkışları içeren bu gruba sahip diğer yapılandırmaların anahtar dosyaları olamaz. Yükleyici düzenleyiciler kurallı adların ve grupların görünen adlarının yanı sıra bir anahtar dosyasının varlığını kabul eder ve yapılandırmalara bağlı olarak değiştirmeyin.

 Bir projede `IVsOutputGroup` paketlemek veya dağıtmak istemediğiniz bir proje varsa, bu çıktıyı bir gruba yerleştirmemeye yeterli olduğunu unutmayın. Bu çıktı, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> Gruplandırmadan bağımsız olarak tüm yapılandırma çıkışlarını döndüren yöntemi uygulayarak normal olarak listelenebilir.

 Daha fazla bilgi için, bkz `IVsOutputGroup` . [Projeler Için MPF](https://github.com/tunnelvisionlabs/MPFProj10)konumundaki özel proje örneğinde uygulama.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
- [Çözüm yapılandırması](../../extensibility/internals/solution-configuration.md)
