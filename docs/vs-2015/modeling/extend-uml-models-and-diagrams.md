---
title: UML modellerini ve diyagramlarını genişletin | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f4c490abbcd5b970c5bf9586ea881be4c5d62a4
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302331"
---
# <a name="extend-uml-models-and-diagrams"></a>UML modellerini ve diyagramları genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, Visual Studio ile birlikte verilen UML modelleme araçlarını genişletmenin farklı yollarını özetler. Visual Studio'nun hangi sürümlerinin her model türünü ve aracını desteklediğini görmek [için mimari ve modelleme araçları için Sürüm desteğine](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)bakın.

 Aşağıdaki örnek senaryoda Fabrikam havaalanı bagaj taşıma sistemleri tasarlar ve kurar. Bir havaalanı projesinden diğerine, temel ekipman ve onu kontrol eden yazılımda birçok benzerlik vardır. Ancak, konveyör bantları, checkin masaları, depolama kutuları ve diğer çanta taşıma ekipmanları nın konfigürasyonu gibi büyük ölçüde değişen çeşitli faktörler de vardır.

 Fabrikam ekibi, yeni bir projeye başlarken, bu gereksinimleri kendi aralarında ve müşterileriyle tartışmalarına yardımcı olacak bir UML modeli oluşturur. Her ekipman parçasını temsil eden nesne düğümleri ile çantaların akışını temsil etmek için etkinlik diyagramları kullanırlar. UML modeli doğrudan sistemin kodunu temsil etmez.

 Fabrikam'ın araç ekibi geliştirme ekiplerine yardımcı olmak için bir dizi geliştirme yapar. Aşağıdaki bölümlerde tanımlayabileceğiniz farklı uzantı türlerini açıklayınız. Bu tekniklerden birkaçını tek bir Visual Studio uzantısında birleştirebilirsiniz.

 Daha fazla bilgi için, bu videoya bakın: video YA ![TIK](../data-tools/media/playvideo.gif "Videoyu Oynat")[I Serisi: UML Araçları ve Genişletilebilirlik](https://msdn.microsoft.com/vstudio/ff859492).

## <a name="requirements"></a><a name="Requirements"></a>Gereksinim -leri

- [Görsel Stüdyo SDK](../extensibility/visual-studio-sdk.md).

- [Visual Studio 2015 için Modelleme SDK](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Profiller
 Profiller, UML öğelerinde stereotipleri ve ek özellikleri tanımlamanıza izin sağlar.

 Fabrikam'ın araç geliştiricileri, «konveyör bandı» ve «checkin masası» gibi etkinlik diyagramlarının nesne düğümleri üzerinde stereotipler tanımlar. Bir ekip üyesi bir etkinlik diyagramı kullanarak bir bagaj taşıma şeması oluşturduğunda, artık her düğümün ne tür bir ekipmanı temsil ettiğini belirtmek için stereotipler ayarlayabilir. Araç geliştiricileri, kullanıcıların konveyör bandının kapasitesi ve iade masasının teslimi gibi değerleri kaydedebilmeleri için bazı stereotiplerde ek özellikler tanımlar.

 Daha fazla bilgi için [uml'u genişletmek için profil tanımlayın'a](../modeling/define-a-profile-to-extend-uml.md)bakın.

## <a name="custom-toolbox-items"></a>Özel Araç Kutusu Öğeleri
 Özel bir araç kutusu öğesi, diyagramda tanımladığınız bir prototipten bir öğe veya öğe grubu oluşturur. Örneğin, belirli bir renk veya stereotipteki kullanım örnekleri veya tasarım deseni temsil eden bir grup sınıf ve ilişkilendirme oluşturan bir araç oluşturabilirsiniz. Bu araç kutusu öğelerini Visual Studio uzantılarına ekleyebilir ve diğer kullanıcılara dağıtabilirsiniz.

 Daha fazla bilgi için [bkz.](../modeling/define-a-custom-modeling-toolbox-item.md)

## <a name="validation"></a>Doğrulama
 UML modelinin belirtilen kısıtlamalara uyduğından emin olmak için kurallar tanımlayabilirsiniz.

 Fabrikam'ın araç geliştiricileri, ekip üyelerinin bagaj taşıma modellerinde basit hatalardan kaçınmalarına yardımcı olacak kurallar tanımlar. Örneğin, iade masası doğrudan bir depolama kutusuna bağlanamaz. En azından aralarında bir konveyör bandı olmalı.

 Daha fazla bilgi için [UML modelleri için doğrulama kısıtlamalarını tanımla'ya](../modeling/define-validation-constraints-for-uml-models.md)bakın.

## <a name="menu-commands"></a>Menü Komutları
 UML diyagramında sağ tıklatarak kullanıcıların çağırabileceği komutları tanımlayabilirsiniz. Komutlar modeli ve diyagramları güncelleştirebilir veya [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]'deki diğer işlemleri gerçekleştirebilir.

 Fabrikam, iade masası oluşturmak ve seçili bir konveyör bandına bağlamak veya diyagramı şirketin düzen kurallarına göre yeniden düzenlemek gibi sık gerçekleştirilen işlemleri otomatikleştirmek için menü komutlarını tanımlar.

 Bkz. [Modelleme diyagramında menü komutunu tanımlayın.](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

## <a name="gestures"></a>Hareketler
 Kullanıcıların başlattığı komutları bir diyagram öğesini çift tıklatarak veya diyagramdaki bir diyagrama veya öğeye sürükleyerek tanımlayabilirsiniz. Diğer UML diyagramlarından, Visual Studio'nun diğer bölümlerinden veya diğer uygulamalardan veya Windows Gezgini'nden (veya Dosya Gezgini) sürüklenen öğelerle başa çıkabilen komutlar tanımlayabilirsiniz.

 Fabrikam ekip üyeleri, belirtim gibi bir dosyayı Windows masaüstünden sürükleyerek herhangi bir model öğesiyle ilişkilendirebilir. Araç geliştiricileri, herhangi bir öğeyi dosya yolu özelliğiyle sağlayan bir stereotip ve bir dosya öğenin üzerine bırakıldığında stereotipi ve dosya yolunu ayarlayan bir hareket tanımlamıştır.

 Daha fazla bilgi için [bkz.](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)

## <a name="responding-to-changes"></a>Değişikliklere Yanıt Verme
 Kullanıcı eylemleri veya başka bir program kodu ndan kaynaklanan modeldeki değişikliklere yanıt veren kod yazabilirsiniz.

 Fabrikam'ın geliştiricileri, klişesine bağlı bir öğenin rengini otomatik olarak ayarlayan kod lar oluşturur. Bu, kullanıcıların modellerdeki öğelerin oynadığı farklı rolleri ayırt etmesini kolaylaştırır.

 Daha fazla bilgi için [bkz: UML Modelindeki Değişikliklere Yanıt](../misc/how-to-respond-to-changes-in-a-uml-model.md)ver.

## <a name="model-bus"></a>Model Otobüs
 Model Veri Günü, bir diyagrama veya modele [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] başka bir diyagramdan veya başka bir Uzantıdan erişmenizi sağlar. Diğer şeylerin yanı sıra, bu birden fazla model arasında bilgi yaymak için izin verir, böylece birkaç kişi aynı anda kombine modeli üzerinde çalışabilir.

 Fabrikam, bagaj taşıma ekipmanlarını temsil etmek için etkinlik diyagramlarında elemanlar kullanır. Her ekipman öğesi, başka bir modelde olabilecek başka bir diyagramda daha ayrıntılı bir belirtime sahip olabilir. Bagaj akış diyagramındaki doğrulama kısıtlamaları, ekipmanın ilgili özelliklerini diğer diyagramlardan alabilir. Diğer diyagramlara yapılan başvurular stereotiplerde tanımlanan ek özelliklerde depolanır.

 Daha fazla bilgi için [UML modellerini diğer modeller ve araçlarla tümleştir'e](../modeling/integrate-uml-models-with-other-models-and-tools.md)bakın.

## <a name="generation"></a>Nesil
 Bir modelden, program kodu, komut dosyaları, yapılandırmalar, belgeler, yeni modeller veya diğer yapılar oluşturabilirsiniz.

 Fabrikam'ın tasarladığı bagaj sistemlerinde, program kodunun çoğu bir projeden diğerine aynıdır. Önemli değişken yönü havaalanı etrafında bagaj akışı planıdır. Tasarım ekibi ilk birkaç projesinin deneyimini yaşadıktan sonra, araç geliştiricileri bagaj akışı modelinden değişken program kodunun ve kullanıcı belgeleri gibi diğer dosyaların çoğunu oluşturan bir şablon oluşturur. Bu, her yeni proje için geliştirme süresini ve hata oranını önemli ölçüde azaltır.

 Daha fazla bilgi için [uml modelinden dosya oluştur'a](../modeling/generate-files-from-a-uml-model.md)bakın.

## <a name="team-foundation-server-integration"></a>Takım Vakfı Sunucu Entegrasyonu
 Çalışma öğelerini model öğelerine bağlayabilir ve bağlı öğelere programlı olarak erişebilirsiniz.

 Fabrikam'ın araç geliştiricileri, her havaalanı projesi için bir çalışma programı oluşturan bir araç yazar. Zamanlamadaki çalışma öğeleri model öğelerine bağlıdır.

 Daha fazla bilgi için [bkz.](../modeling/define-a-work-item-link-handler.md)

## <a name="tools-that-update-models"></a>Modelleri Güncelleyen Araçlar
 UML modellerini yükleyebilen tek başına uygulamalar ve Visual Studio uzantıları oluşturabilirsiniz.

 Fabrikam'ın geliştiricileri bir modeli okuyan ve modelin her öğesi üzerinde çalışmanın ilerleme raporları oluşturan bir araç oluşturur.

 Daha fazla bilgi için [bkz.](../modeling/read-a-uml-model-in-program-code.md)

## <a name="domain-specific-languages"></a>Etki Alanına Özgü Diller
 Belirli bir model türünü sık sık kullandığınızda, etki alanına özgü bir dil oluşturmak yararlı olabilir. Bu, iş ihtiyaçlarınıza bir UML modelinden daha yakın bir şekilde uyacak şekilde yapılabilir, ancak bunu oluşturmak ve sürdürmek için daha fazla çaba gerektirir. Daha fazla bilgi için [Visual Studio - Etki Alanına Özel Diller için Modelleme SDK'ya](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)bakın.

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|------------------|---------------|
|**Videolar**|![video](../data-tools/media/playvideo.gif "Videoyu Oynat") [MSDN bağlantı Nasıl Serisi mi: UML Araçları ve Genişletilebilirlik](https://msdn.microsoft.com/vstudio/ff859492)<br /><br /> ![video](../data-tools/media/playvideo.gif "Videoyu Oynat") Kanal 9 [bağlantı: VISUAL Studio ile UML](https://channel9.msdn.com/posts/clinted/)|
|**Forumlar**|-   [Visual Studio Visualization & Modelleme Araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modelleme SDK (DSL Araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Bloglar**|[Visual Studio ALM + Team Vakfı Server Blog](https://blogs.msdn.com/b/visualstudioalm)|
|**Teknik Makaleler ve Dergiler**|[MSDN Mimarlık Merkezi](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML Modelleme Genişletilebilirliği için](../modeling/api-reference-for-uml-modeling-extensibility.md) [uygulama API](../modeling/create-models-for-your-app.md) Başvurusu için modeller oluşturun
