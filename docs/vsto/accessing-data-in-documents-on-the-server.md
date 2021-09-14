---
title: Sunucudaki belgelerdeki verilere erişin
description: Microsoft Office Word veya Microsoft Office Excel nesne modelini kullanmak zorunda kalmadan belge düzeyi özelleştirmesindeki verilere karşı nasıl programlama yapabileceğinizi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725618"
---
# <a name="access-data-in-documents-on-the-server"></a>Sunucudaki belgelerdeki verilere erişin
  Microsoft Office Word veya Microsoft Office Excel nesne modelini kullanmak zorunda kalmadan belge düzeyi özelleştirmesindeki verilere karşı programlama yapabilirsiniz. bu, Word veya Excel yüklü olmayan bir sunucuda bulunan bir belgede bulunan verilere erişebileceğiniz anlamına gelir. Örneğin, bir sunucudaki kod (örneğin, bir [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sayfada) bir belgedeki verileri özelleştirebilir ve özelleştirilmiş belgeyi bir son kullanıcıya gönderebilir. Son Kullanıcı belgeyi açtığında, çözüm derlemesinde veri bağlama kodu özelleştirilmiş verileri belgeye bağlar. Belgedeki veriler kullanıcı arabiriminden ayrıldığından bu mümkündür. Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Sunucuda kullanılmak üzere verileri önbelleğe alma
 Belgedeki bir veri nesnesini önbelleğe almak için, <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> tasarım zamanında özniteliği ile işaretleyin veya `StartCaching` çalışma zamanında bir konak öğesinin yöntemini kullanın. Belgedeki bir veri nesnesini önbelleğe aldığınızda, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nesneyi belgede depolanan BIR XML dizesine dizileştirir. Nesnelerin önbelleğe almak için uygun gereksinimleri karşılaması gerekir. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

 Sunucu tarafı kod, veri önbelleğindeki tüm veri nesnelerini işleyebilir. Önbelleğe alınmış veri örneklerine bağlı denetimler Kullanıcı arabirimiyle eşitlenir, böylece verilerde yapılan tüm sunucu tarafı değişiklikleri, belge istemcide açıldığında otomatik olarak görünür.

## <a name="access-data-in-the-cache"></a>Önbellekteki verilere erişin
 önbellekteki verilere, örneğin bir konsol uygulamasından, bir Windows Forms uygulamadan veya bir Web sayfasından Office dışındaki uygulamalardan erişebilirsiniz. Önbelleğe alınmış verilere erişen uygulamanın tam güven olması gerekir; kısmi güveni olan bir Web uygulaması, bir Office belgesinde önbelleğe alınmış verileri ekleyemez, alamaz veya değiştiremezler.

 Veri önbelleğine, sınıfının özelliği tarafından açığa çıkarılan koleksiyonlar hiyerarşisi aracılığıyla erişilebilir <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> :

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>Özelliği <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> , belge düzeyi özelleştirmesindeki tüm önbelleğe alınmış verileri içeren bir döndürür.

- Her biri <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> bir veya daha fazla <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> nesne içerir. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>, Tek bir sınıfta tanımlanan önbelleğe alınmış veri nesnelerinin tümünü içerir.

- Her biri <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> bir veya daha fazla <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nesne içerir. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>Tek bir önbelleğe alınmış veri nesnesini temsil eder.

  aşağıdaki kod örneğinde, `Sheet1` bir Excel çalışma kitabı projesinin sınıfında önbelleğe alınmış bir dizeye nasıl erişebileceğiniz gösterilmektedir. Bu örnek, yöntemi için sağlanmış daha büyük bir örneğin bir parçasıdır <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> .

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>Önbellekteki verileri değiştirme
 Önbelleğe alınmış bir veri nesnesini değiştirmek için genellikle aşağıdaki adımları gerçekleştirirsiniz:

1. Önbelleğe alınmış nesnenin XML gösterimini nesnenin yeni bir örneğine serisini kaldırma. XML 'e, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> önbelleğe alınmış veri nesnesini temsil eden öğesinin özelliğini kullanarak erişebilirsiniz.

2. Bu kopyada değişiklikleri yapın.

3. Değiştirilen nesneyi, aşağıdaki seçeneklerden birini kullanarak veri önbelleğine geri doğru bir şekilde seri hale getirme:

    - Değişiklikleri otomatik olarak seri hale getirmek istiyorsanız <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> yöntemini kullanın. Bu yöntem veri önbelleğinde  seri hale getirmek <xref:System.Data.DataSet> , <xref:System.Data.DataTable> ve türü belirtilmiş veri kümesi nesneleri için DiffGram biçimini kullanır. **DiffGram** biçimi çevrimdışı bir belgedeki veri önbelleğinde yapılan değişikliklerin sunucuya doğru şekilde gönderilmesini sağlar.

    - Önbelleğe alınan verilerde yapılan değişiklikler için kendi serileştirme işlemini gerçekleştirmek istiyorsanız, doğrudan <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> özelliğine yazabilirsiniz. Bir  <xref:System.Data.Common.DataAdapter> veritabanını <xref:System.Data.DataSet> ,, <xref:System.Data.DataTable> veya türü belirtilmiş veri kümesindeki verilerde yapılan değişikliklerle güncelleştirmek için kullanıyorsanız, DiffGram biçimini belirtin. Aksi takdirde, <xref:System.Data.Common.DataAdapter> mevcut satırları değiştirmek yerine yeni satırlar ekleyerek veritabanını güncelleştirir.

### <a name="modify-data-without-deserializing-the-current-value"></a>Geçerli değerin serisini kaldırmadan verileri Değiştir
 Bazı durumlarda, önbelleğe alınmış nesnenin değerini, önce geçerli değeri seri durumdan kaldırmadan değiştirmek isteyebilirsiniz. Örneğin, bir dize veya tamsayı gibi basit bir türe sahip bir nesnenin değerini değiştiriyorsanız veya bir sunucuda önbelleğe alınmış bir belgeyi başlatırken bunu yapabilirsiniz <xref:System.Data.DataSet> . Bu durumlarda, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> önce önbelleğe alınmış nesnenin geçerli değerini seri durumdan çıkarmak zorunda kalmadan yöntemini kullanabilirsiniz.

 aşağıdaki kod örneği, `Sheet1` bir Excel çalışma kitabı projesinin sınıfında, önbelleğe alınmış bir dizenin değerinin nasıl değiştirileceğini gösterir. Bu örnek, yöntemi için sağlanmış daha büyük bir örneğin bir parçasıdır <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>Veri önbelleğindeki null değerleri Değiştir
 Veri önbelleği, belge kaydedilip kapatıldığında **null** değeri olan nesneleri depolamaz. Önbelleğe alınmış verileri değiştirirken bu sınırlamanın çeşitli sonuçları vardır:

- Veri önbelleğindeki herhangi bir nesneyi **null** değerine ayarlarsanız, belge açıldığında veri önbelleğindeki tüm nesneler otomatik olarak **null** olarak ayarlanır ve belge kaydedilip kapatıldığında tüm veri önbelleğinin temizlenmesi gerekir. Diğer bir deyişle, önbelleğe alınmış tüm nesneler veri önbelleğinden kaldırılır ve <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> koleksiyon boş olur.

- Veri önbelleğinde **null** nesnelerle bir çözüm oluşturursanız ve <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> belge ilk kez açılmadan önce sınıfını kullanarak bu nesneleri başlatmak istiyorsanız, veri önbelleğindeki tüm nesneleri başlattığınızdan emin olmanız gerekir. Nesneleri yalnızca bir kısmını başlattığınızda, belge açıldığında tüm nesneler **null** olarak ayarlanır ve belge kaydedilip kapatıldığında tüm veri önbelleğinin temizlenmesi gerekir.

## <a name="access-typed-datasets-in-the-cache"></a>Önbellekte yazılan veri kümelerine erişme
 türü belirlenmiş bir veri kümesindeki verilere hem Office çözümünden hem de bir Windows Forms uygulaması ya da bir proje gibi Office dışındaki bir uygulamadan erişmek istiyorsanız [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] , türü belirtilmiş veri kümesini her iki projede de başvurulan ayrı bir derlemede tanımlamanız gerekir. **veri kaynağı yapılandırma** sihirbazı 'nı veya **Veri Kümesi Tasarımcısı** kullanarak her bir projeye türü belirtilmiş veri kümesini eklerseniz, .NET Framework iki projedeki türü belirtilmiş veri kümelerini farklı türler olarak değerlendirir. Türü belirtilmiş veri kümeleri oluşturma hakkında daha fazla bilgi için bkz. [Visual Studio veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sunucudaki belgelerdeki verilere erişin](../vsto/accessing-data-in-documents-on-the-server.md)
- [Belge düzeyi Özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)