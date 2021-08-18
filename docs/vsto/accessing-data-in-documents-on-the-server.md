---
title: Sunucu belgelerde verilere erişme
description: Word veya Microsoft Office nesne modelini kullanmak zorunda kalmadan belge düzeyi özelleştirmede verilere karşı program Microsoft Office Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 21723deada493dd5e3d6ab6a16c6dc6366829bbb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135578"
---
# <a name="access-data-in-documents-on-the-server"></a>Sunucu belgelerde verilere erişme
  Word veya Microsoft Office Excel'nin nesne modelini kullanmak zorunda kalmadan, belge düzeyi Microsoft Office özelleştirmede verilere karşı program Microsoft Office Excel. Bu, Word veya Excel yüklü bir sunucu üzerinde belge içinde yer alan verilere erişebilirsiniz. Örneğin, bir sunucu üzerinde kod (örneğin, bir sayfada), bir belgede verileri özelleştirilebilir ve özelleştirilmiş [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] belgeyi son kullanıcıya gönderebilir. Son kullanıcı belgeyi açtığında, çözüm derlemesinde veri bağlama kodu özelleştirilmiş verileri belgeye bağlar. Belgede yer alan veriler kullanıcı arabiriminden ayrıldığından bu mümkündür. Daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler.](../vsto/cached-data-in-document-level-customizations.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Sunucuda kullanmak üzere verileri önbelleğe alın
 Bir belgede bir veri nesnesini önbelleğe etmek için tasarım zamanında özniteliğiyle işaretlerini ekleyin veya çalışma zamanında <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> `StartCaching` bir konak öğesinin yöntemini kullanın. Bir belgede bir veri nesnesini önbelleğe alır, nesne belgede [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] depolanan bir XML dizesinde seri hale. Nesnelerin önbelleğe almaya uygun olması için belirli gereksinimleri karşılaması gerekir. Daha fazla bilgi için [bkz. Verileri önbelleğe alın.](../vsto/caching-data.md)

 Sunucu tarafı kodu, veri önbelleğinde herhangi bir veri nesnelerini işabilir. Önbelleğe alınan veri örneklerine bağlı denetimler kullanıcı arabirimiyle eşitlenir, böylece verilerde yapılan tüm sunucu tarafı değişiklikleri, belge istemcide açıldığında otomatik olarak ortaya açılır.

## <a name="access-data-in-the-cache"></a>Önbellekte verilere erişme
 Önbellekte yer alan verilere bir konsol Office, Windows Forms uygulaması veya Web sayfası gibi uygulamaların dışından erişebilirsiniz. Önbelleğe alınan verilere erişen uygulamanın tam güveni olması gerekir; kısmi güveni olan bir Web uygulaması, bir belgede önbelleğe alınmış verileri ek Office veya değiştiremez.

 Veri önbelleğine, sınıfının özelliği tarafından ortaya çıkarılma koleksiyon <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> hiyerarşisi aracılığıyla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> erişilebilir:

- özelliği, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> belge <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> düzeyinde özelleştirmede önbelleğe alınan tüm verileri içeren bir döndürür.

- Her <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> biri bir veya daha fazla nesne <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> içerir. , <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> tek bir sınıf içinde tanımlanan tüm önbelleğe alınmış veri nesnelerini içerir.

- Her <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> biri bir veya daha fazla nesne <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> içerir. , <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> önbelleğe alınmış tek bir veri nesnesini temsil eder.

  Aşağıdaki kod örneği, bir Excel çalışma kitabı projesinin sınıfında `Sheet1` önbelleğe alınmış bir dizeye erişmeyi gösterir. Bu örnek, yöntemi için sağlanan daha büyük bir örneğin bir <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> parçasıdır.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>Önbellekte verileri değiştirme
 Önbelleğe alınmış bir veri nesnesini değiştirmek için genellikle aşağıdaki adımları gerçekleştirebilirsiniz:

1. Önbelleğe alınan nesnenin XML gösterimini nesnesinin yeni bir örneğinde deserialize. ÖNBELLEĞE alınan veri nesnesini temsil <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> eden özelliğini <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> kullanarak XML'ye erişebilirsiniz.

2. Bu kopyada değişiklik yapın.

3. Aşağıdaki seçeneklerden birini kullanarak değiştirilen nesneyi veri önbelleğine geri seri hale getirme:

    - Değişiklikleri otomatik olarak serileştirmek için yöntemini <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> kullanın. Bu yöntem, veri önbelleğinde , ve türüne sahip veri kümesi nesnelerini seri hale getirme için **DiffGram** <xref:System.Data.DataSet> biçimini <xref:System.Data.DataTable> kullanır. **DiffGram** biçimi, çevrimdışı bir belgede veri önbelleğinde yapılan değişikliklerin sunucuya doğru şekilde gönderilmesini sağlar.

    - Önbelleğe alınan verilerde yapılan değişiklikler için kendi serileştirmenizi gerçekleştirmek için doğrudan özelliğine <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> yazabilirsiniz. Bir veritabanını , veya türünde bir veri kümesinde yapılan değişikliklerle güncelleştirmek için kullanıyorsanız **DiffGram** <xref:System.Data.Common.DataAdapter> <xref:System.Data.DataSet> biçimini <xref:System.Data.DataTable> belirtin. Aksi <xref:System.Data.Common.DataAdapter> takdirde, var olan satırları değiştirmek yerine yeni satırlar ekleyerek veritabanını güncelleştirecek.

### <a name="modify-data-without-deserializing-the-current-value"></a>Geçerli değerin deserializing olmadan verileri değiştirme
 Bazı durumlarda, önce geçerli değerinrializing önce olmadan önbelleğe alınan nesnenin değerini değiştirmek istiyor olabilir. Örneğin, dize veya tamsayı gibi basit bir türe sahip bir nesnenin değerini değiştiriyorsanız veya bir sunucu üzerinde önbelleğe alınmış bir belgeyi başlatarak bunu <xref:System.Data.DataSet> yapabiliriz. Bu durumlarda, önbelleğe alınan nesnenin <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> geçerli değerini önce deserializing olmadan yöntemini kullanabilirsiniz.

 Aşağıdaki kod örneği, bir Excel çalışma kitabı projesinin sınıfında önbelleğe `Sheet1` alınmış bir dizenin değerinin nasıl değiştiril olduğunu gösterir. Bu örnek, yöntemi için sağlanan daha büyük bir örneğin bir <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> parçasıdır.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>Veri önbelleğinde null değerleri değiştirme
 Veri önbelleği, belge kaydedilebilir ve kapatılan **null** değerine sahip nesneleri depolamaz. Bu sınırlama, önbelleğe alınmış verileri değiştirerek birkaç sonuç doğurur:

- Veri önbelleğinde herhangi bir nesneyi **null** değerine ayarsanız, belge açıldığında veri önbelleğinde yer alan tüm nesneler otomatik olarak **null** olarak ayarlanır ve belge kaydedilen ve kapatılan veri önbelleğinin tamamı temizlenir. Diğer bir ifadeyle, önbelleğe alınan tüm nesneler veri önbelleğinden kaldırılır ve <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> koleksiyon boş olur.

- Veri önbelleğinde **null** nesnelere sahip bir çözüm oluşturursanız ve belge ilk kez başlatılmadan önce sınıfını kullanarak bu nesneleri başlatmak istiyorsanız, veri önbelleğinde tüm nesneleri başlatmak istediğinizden emin olmak <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> gerekir. Yalnızca bazı nesneleri başlatacak olursanız, belge açıldığında tüm nesneler **null** olarak ayarlanır ve belge kaydedilen ve kapatılan veri önbelleğinin tamamı temizlenmiş olur.

## <a name="access-typed-datasets-in-the-cache"></a>Önbellekte türü türü alınmış veri kümelerine erişme
 Hem Office çözümünden hem de Windows Forms uygulaması veya proje gibi Office dışındaki bir uygulamanın türüne sahip bir veri kümesinde yer alan verilere erişmek için, türüne sahip veri kümesini her iki projede de başvurulan ayrı bir derlemede tanımlamanız [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] gerekir. Veri Kaynağı Yapılandırma sihirbazını veya **Veri Kümesi Tasarımcısı'yi** kullanarak her bir projeye türü yazıldı veri kümesi eklersiniz, .NET Framework iki projede türü farklı türlerde olan veri kümelerini işler.  Türü yazılan veri kümeleri oluşturma hakkında daha fazla bilgi için bkz. Veri [kümelerini](../data-tools/create-and-configure-datasets-in-visual-studio.md)Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md)
- [Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)