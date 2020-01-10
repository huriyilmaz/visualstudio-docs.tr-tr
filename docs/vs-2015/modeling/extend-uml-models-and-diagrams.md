---
title: UML modellerini ve Diyagramları Genişletme | Microsoft Docs
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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849799"
---
# <a name="extend-uml-models-and-diagrams"></a>UML modellerini ve diyagramları genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, Visual Studio 'Ya dahil edilen UML modelleme araçlarını genişletebilmeniz için kullanabileceğiniz farklı yollar özetlenmektedir. Hangi Visual Studio sürümlerinin her model türünü ve aracını desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Aşağıdaki örnek senaryoda Fabrikam, Havaalanı Bagaj işleme sistemlerini tasarlar ve kurar. Bir havaalanı projesinden sonrakine, temel ekipman ve bunu denetleyen yazılımda birçok benzerlikler vardır. Ancak, taşıyıcı belts, iade masaları, depolama alanı bölmeleri ve diğer paket işleme donanımının yapılandırması gibi birçok farklı etken de vardır.

 Yeni bir proje başlatırken fabrikam ekibi, bu gereksinimleri kendi müşterileri arasında tartışmaya yardımcı olmak için bir UML modeli oluşturur. Bu kullanıcılar, her bir ekipman parçasını temsil eden nesne düğümleri ile, her bir ekipman parçasını temsil eden bir veya daha fazla sayıda UML modeli, sistem kodunu doğrudan temsil etmez.

 Fabrikam 'ın araçlar ekibi, geliştirme ekiplerine yardımcı olmak için bir dizi geliştirme yapar. Aşağıdaki bölümlerde, tanımlayabilmeniz gereken farklı uzantı türleri açıklanır. Bu tekniklerin birçoğunu tek bir Visual Studio uzantısı içinde birleştirebilirsiniz.

 Daha fazla bilgi için bkz. Bu video: ![video MSDN 'ye bağlantı](../data-tools/media/playvideo.gif "PlayVideo")[MSDN nasıl yapılır serisi: UML araçları ve genişletilebilirliği](https://msdn.microsoft.com/vstudio/ff859492).

## <a name="Requirements"></a> Gereksinimleri

- [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

- [Visual Studio 2015 Için modelleme SDK](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Profiller
 Profiller UML öğelerinde stereotipler ve ek özellikler tanımlamanızı sağlar.

 Fabrikam 'ın araç geliştiricileri, «taşıyıcı bandı» ve «checkin masası» gibi Etkinlik diyagramlarındaki nesne düğümlerinde stereotipler tanımlar. Bir takım üyesi bir etkinlik diyagramı kullanarak Bagaj işleme düzeni oluşturduğunda, artık stereotipleri her bir düğümün hangi türde bir temsil ettiğini belirtecek şekilde ayarlayabilirler. Araç geliştiricileri bazı stereotiplerde ek özellikler tanımlar, böylece kullanıcılar bir taşıyıcı bandın kapasitesi ve bir iade masasının kullanımı gibi değerleri kaydedebilir.

 Daha fazla bilgi için bkz. [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).

## <a name="custom-toolbox-items"></a>Özel araç kutusu öğeleri
 Özel araç kutusu öğesi bir diyagramda tanımladığınız prototipten bir öğe veya öğe grubu oluşturur. Örneğin, belirli bir renk veya stereotipe veya bir tasarım modelini temsil eden bir sınıf ve ilişkilendirmeler grubuna kullanım durumları oluşturan bir araç oluşturabilirsiniz. Bu araç kutusu öğelerini Visual Studio uzantılarına ekleyebilir ve bunları diğer kullanıcılara dağıtabilirsiniz.

 Daha fazla bilgi için bkz. [Özel Modelleme Araç kutusu öğesi tanımlama](../modeling/define-a-custom-modeling-toolbox-item.md).

## <a name="validation"></a>Doğrulama
 Bir UML modelinin belirtilen kısıtlamalara uygun olduğundan emin olmak için kurallar tanımlayabilirsiniz.

 Fabrikam 'ın araç geliştiricileri, takım üyelerinin Bagaj işleme modellerinde basit hatalardan kaçınmanıza yardımcı olacak kurallar tanımlar. Örneğin, bir iade etme masası doğrudan bir depolama sepetine bağlanamaz. Aralarında en az bir taşıyıcı bant olmalıdır.

 Daha fazla bilgi için bkz. [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="menu-commands"></a>Menü Komutları
 Kullanıcıların bir UML diyagramında öğelere sağ tıklayıp çağırabileceği komutları tanımlayabilirsiniz. Komutlar modeli ve diyagramları güncelleştirebilir veya [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]başka işlemler gerçekleştirebilir.

 Fabrikam, bir iade masası oluşturma ve onu seçili bir taşıyıcı bandına bağlama veya bir diyagramı şirketin düzen kurallarına göre yeniden düzenleme gibi sık gerçekleştirilen işlemleri otomatikleştirmek için menü komutlarını tanımlar.

 Bkz. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="gestures"></a>Hareketler
 Kullanıcıların Başlatan komutları bir diyagram öğesine çift tıklayarak ya da diyagramdaki bir diyagrama veya bir öğeye sürükleyerek tanımlayabilirsiniz. Diğer UML diyagramlarından, Visual Studio 'nun diğer bölümlerinden veya diğer uygulamalardan veya Windows Gezgini 'nden (veya dosya Gezgini 'nden) sürüklenen öğeler ile ilgilenebilmeniz gereken komutlar tanımlayabilirsiniz.

 Fabrikam ekip üyeleri, bir belirtim gibi bir dosyayı Windows masaüstünden sürükleyerek herhangi bir model öğesiyle ilişkilendirebilir. Araç geliştiricileri, bir dosya yolu özelliği olan herhangi bir öğe sağlayan bir stereotip ve bir dosya bir öğe üzerinde bırakıldığında stereotipi ve dosya yolunu ayarlayan bir hareket tanımladı.

 Daha fazla bilgi için bkz. [Modelleme diyagramında hareket Işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="responding-to-changes"></a>Değişikliklere yanıt verme
 Modeldeki değişikliklere yanıt veren kodu, Kullanıcı eylemlerinin veya diğer program kodu tarafından mı kaynaklanabileceğini yazabilirsiniz.

 Fabrikam 'ın geliştiricileri, kendi stereotipine bağlı bir öğenin rengini otomatik olarak ayarlayan kodu oluşturur. Bu, kullanıcıların modellerdeki öğelerle oynanan farklı rolleri ayırt etmelerini kolaylaştırır.

 Daha fazla bilgi için bkz. [nasıl yapılır: UML modeldeki değişikliklere yanıt verme](../misc/how-to-respond-to-changes-in-a-uml-model.md).

## <a name="model-bus"></a>Model veri yolu
 Model veri yolu, başka bir diyagramdan veya başka bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısından bir diyagrama veya modele erişmenizi sağlar. Bunun yanı sıra, birden fazla kişinin aynı anda birleştirilmiş modelde çalışabilmesi için birden fazla model arasında bilgi yaymanızı sağlar.

 Fabrikam, Bagaj işleme donanımını göstermek için Etkinlik diyagramlarındaki öğeleri kullanır. Her bir ekipman öğesi, başka bir modelde olabilen başka bir diyagramda daha ayrıntılı bir belirtime sahip olabilir. Bagaj akış diyagramındaki doğrulama kısıtlamaları, donatımın ilgili özelliklerini diğer diyagramlardan alabilir. Diğer diyagramların başvuruları, stereotiplerde tanımlanan ek özelliklerde depolanır.

 Daha fazla bilgi için bkz. [UML modellerini diğer modeller ve araçlarla tümleştirme](../modeling/integrate-uml-models-with-other-models-and-tools.md).

## <a name="generation"></a>Nesil
 Bir modelden program kodu, betikler, konfigürasyonlar, belgeler, yeni modeller veya diğer yapıtlar oluşturabilirsiniz.

 Fabrikam 'ın tasarlayan Bagaj sistemlerinde, program kodunun büyük bölümü bir projeden sonrakine aynı olur. Ana değişken en önemli değeri, Havaalanı çevresindeki bagaj akışının planlayıcıdır. Tasarım ekibinin ilk birkaç projesi deneyimiyle karşılaşdıktan sonra, araç geliştiricileri Bagaj akış modelinden, değişken program kodunun ve Kullanıcı belgeleri gibi diğer dosyaların çoğunun oluşturduğu bir şablon oluşturur. Bu, her yeni proje için geliştirme süresini ve hata oranını önemli ölçüde azaltır.

 Daha fazla bilgi için bkz. [UML modelden dosya oluşturma](../modeling/generate-files-from-a-uml-model.md).

## <a name="team-foundation-server-integration"></a>Team Foundation Server Tümleştirme
 İş öğelerini model öğelerine bağlayabilir ve bağlantılı öğelere programlı bir şekilde erişebilirsiniz.

 Fabrikam 'ın araç geliştiricileri, her Havaalanı projesi için bir iş zamanlaması üreten bir araç yazar. Zamanlamadaki iş öğeleri model öğeleriyle bağlantılıdır.

 Daha fazla bilgi için bkz. [iş öğesi bağlantı Işleyicisini tanımlama](../modeling/define-a-work-item-link-handler.md).

## <a name="tools-that-update-models"></a>Modelleri güncelleştiren Araçlar
 UML modellerini yükleyeabilecek tek başına uygulamalar ve Visual Studio uzantıları oluşturabilirsiniz.

 Fabrikam geliştiricileri, modeli okuyan ve modelin her öğesinde çalışmanın ilerleme durumunu raporlar üreten bir araç oluşturur.

 Daha fazla bilgi için bkz. [program kodunda BIR UML modeli okuma](../modeling/read-a-uml-model-in-program-code.md).

## <a name="domain-specific-languages"></a>Etki alanına özgü diller
 Belirli türde bir modeli sıklıkla kullandığınız yerde, etki alanına özgü bir dil oluşturmak yararlı olabilir. Bu, işletmenizin ihtiyaçlarını UML modelden daha yakından uydurmak için yapılabilir, ancak bunu oluşturmak ve sürdürmek için daha fazla çaba gerektirir. Daha fazla bilgi için bkz. [Visual Studio Için modelleme sdk-etki alanına özgü diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|------------------|---------------|
|**Videolar**|![video MSDN bağlantısı-](../data-tools/media/playvideo.gif "PlayVideo") [nasıl yapılır serisi: UML araçları ve genişletilebilirliği](https://msdn.microsoft.com/vstudio/ff859492)<br /><br /> ![video](../data-tools/media/playvideo.gif "PlayVideo") [kanalı 9 ' a bağlantı: VISUAL Studio ile UML](https://channel9.msdn.com/posts/clinted/)|
|**Forumlar**|-   [Visual Studio görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio görselleştirme & modelleme SDK (dsl araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Bloglar**|[Visual Studio ALM + Team Foundation Server blogu](https://blogs.msdn.com/b/visualstudioalm)|
|**Teknik makaleler ve Günlükler**|[MSDN mimari Merkezi](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modelleme genişletilebilirliği için uygulama API başvurunuz](../modeling/api-reference-for-uml-modeling-extensibility.md) [için modeller oluşturma](../modeling/create-models-for-your-app.md)
