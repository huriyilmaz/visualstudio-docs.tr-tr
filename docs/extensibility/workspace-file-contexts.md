---
title: Visual Studio 'da çalışma alanı dosya bağlamları | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952873"
---
# <a name="workspace-file-contexts"></a>Çalışma alanı dosya bağlamları

[Açık klasör](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) çalışma alanları içindeki tüm Öngörüler, arabirimi uygulayan "dosya bağlam sağlayıcıları" tarafından oluşturulur <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> . Bu uzantılar, dosya bağlamı tanımlamak için ihtiyaç duydukları öngörüleri biriktirmek için klasörler veya dosyalardaki desenleri arayabilir, MSBuild dosyalarını ve makefiles 'ı tespit edebilir, paket bağımlılıklarını algılayabilir vb.. Tek başına bir dosya bağlamı herhangi bir eylem gerçekleştirmez, bunun yerine başka bir uzantının üzerinde işlem gerçekleştirebileceği verileri sağlar.

Her biri <xref:Microsoft.VisualStudio.Workspace.FileContext> `Guid` kendisiyle ilişkili olan veri türünü tanımlayan bir ile ilişkilendirilir. Çalışma alanı `Guid` daha sonra, özelliği aracılığıyla verileri kullanan uzantılarla eşleştirmek için bunu kullanır <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> . Dosya bağlamı sağlayıcısı, `Guid` için veri üretebileceği dosya bağlamını tanımlayan meta veriler ile birlikte verilir.

Tanımlandıktan sonra bir dosya bağlamı, çalışma alanındaki herhangi bir dosya veya klasör sayısıyla ilişkilendirilebilir. Belirli bir dosya veya klasör, herhangi bir sayıda dosya bağlamlarına ilişkilendirilebilir. Bu, çoktan çoğa bir ilişkidir.

Dosya bağlamları için en yaygın senaryolar derleme, hata ayıklama ve dil hizmetleriyle ilgilidir. Daha fazla bilgi için, bu senaryolarla ilgili diğer konulara bakın.

## <a name="file-context-lifecycle"></a>Dosya bağlamı yaşam döngüsü

A için yaşam ömürleri `FileContext` belirleyici değildir. Her zaman bir bileşen bazı bağlam türleri kümesi için zaman uyumsuz olarak talep edebilir. İstek bağlamı türlerinin bazı alt kümelerini destekleyen sağlayıcılar sorgulanacaktır. `IWorkspace`Örnek, yöntemi aracılığıyla tüketici ve sağlayıcılar arasında orta adam işlevi görür <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> . Tüketiciler bir bağlam isteyebilir ve bağlam temelinde bazı kısa süreli eylemler gerçekleştirebilir, diğerleri bir bağlam isteyebilir ve uzun süreli bir başvuruyu koruyabilir.

Dosya bağlamının güncel hale gelmesine neden olan dosyalarda değişiklikler olabilir. Sağlayıcı, `FileContext` güncelleştirmelerinin tüketicilerini bilgilendirmek için üzerinde bir olay tetikedebilir. Örneğin, bazı dosyalar için bir derleme bağlamı sağlanmışsa ancak bir disk üzerindeki değişiklik bu bağlamı geçersiz kılar, özgün üretici olayı çağırabilir. `FileContext`Daha sonra, daha sonra yeni bir için yeniden sorgulama yapan tüm tüketiciler `FileContext` .

>[!NOTE]
>Tüketicilere gönderim modeli yok. Tüketicilere, bir sağlayıcının istekleri sonrasında yeni bir bildirim alınmayacak `FileContext` .

## <a name="expensive-file-context-computations"></a>Pahalı dosya bağlamı hesaplamaları

Özellikle bir sağlayıcının dosyalar arasındaki ilişkiyi çözümlemesi gerektiğinde diskten dosya içeriğini okumak pahalı olabilir. Örneğin, bir sağlayıcı bir kaynak dosyanın dosya bağlamı için sorgulanabilir, ancak dosya bağlamı bir proje dosyasındaki meta verilere bağımlıdır. Proje dosyasını ayrıştırmak veya MSBuild ile değerlendirmek pahalıdır. Bunun yerine, uzantı, `IFileScanner` `FileDataValue` çalışma alanı dizinleme sırasında veri oluşturmak için bir dışarı aktarabilir. Artık dosya bağlamları sorulduğunda, `IFileContextProvider` bu dizinli verileri hızlı bir şekilde sorgulayabilir. Dizin oluşturma hakkında daha fazla bilgi için bkz. [çalışma alanı dizin oluşturma](workspace-indexing.md) konusu.

>[!WARNING]
>`FileContext`İşlem için pahalı olabilecek diğer yollarla dikkatli olun. Bazı Kullanıcı arabirimi etkileşimleri zaman uyumludur ve yüksek bir istek hacmine bağlıdır `FileContext` . Örnek olarak bir düzenleyici sekmesi açma ve bir **Çözüm Gezgini** bağlam menüsü açma sayılabilir. Bu eylemler birçok derleme bağlamı türü isteği yapar.

## <a name="file-context-related-apis"></a>Dosya bağlamı ile ilgili API 'Ler

- <xref:Microsoft.VisualStudio.Workspace.FileContext> verileri ve meta verileri tutar.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> ve <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> Dosya bağlamını oluşturun.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> dosya bağlamı sağlayıcısını dışa aktarır.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> , kullanıcılar için dosya bağlamlarını almak üzere kullanılır.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Açık klasörün kullanacağı derleme bağlam türlerini tanımlar.

## <a name="file-context-actions"></a>Dosya bağlamı eylemleri

`FileContext`Kendisi bazı dosyalar hakkında yalnızca veri olsa da, <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> Bu verileri hızlı bir şekilde ifade etme ve üzerinde işlem yapmanın bir yoludur. `IFileContextAction` , kullanımında esnektir. En yaygın çalışmalarından ikisi derleme ve hata ayıklama.

## <a name="reporting-progress"></a>İlerlemeyi raporlama

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>Yöntemi geçirilir `IProgress<IFileContextActionProgressUpdate>` , ancak bağımsız değişken bu tür olarak kullanılmamalıdır. `IFileContextActionProgressUpdate` boş bir arabirim olduğundan, çağırma işlemi oluşturabilir `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` `NotImplementedException` . Bunun yerine, `IFileContextAction` senaryonun bağımsız değişkenini senaryo için gereken şekilde başka bir türe ataması gerekir.

Visual Studio tarafından sağlanan türler hakkında daha fazla bilgi için, ilgili senaryonun belgelerine bakın.

## <a name="file-context-action-related-apis"></a>Dosya bağlamı eylemi ilgili API 'Ler

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> , ' a dayalı bazı davranışlar yürütür `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> örneği oluşturur `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> türü dışarı aktarır `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Dosya izleme

Bir çalışma alanı dosya değişikliği bildirimlerini dinler ve aracılığıyla sağlar <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . "ExcludedItems" ayarıyla eşleşen dosyalar, dosya bildirim olayları oluşturmaz. Bildirim basitleştirmesi ve yinelenen azaltma için olaylar arasında bir eşik kullanılır. Bir dosya değişikliğine yanıt vermek istediğinizde, bu hizmete abone olmanız gerekir.

>[!TIP]
>Çalışma alanının [Dizin oluşturma hizmeti](workspace-indexing.md) , varsayılan olarak dosya olaylarına abone olur. Dosya eklemeleri ve değişiklikler `IFileScanner` Bu dosyanın yeni verileri için ilgili s olaylarının çağrılmasına neden olur. Dosya silme, dizinli verileri kaldıracak. Dosya İzleyici hizmetine abone olmanız gerekmez `IFileScanner` .

## <a name="next-steps"></a>Sonraki adımlar

* [Dizin oluşturma](workspace-indexing.md) -çalışma alanı dizin oluşturma, çalışma alanıyla ilgili bilgileri toplar ve sürdürür.
* [Çalışma alanları](workspaces.md) -çalışma alanı kavramlarını ve ayarları depolamayı gözden geçirin.
