---
title: Visual Studio |'de çalışma alanı dosya bağlamları Microsoft Docs
description: Klasör Aç çalışma alanlarıyla ilgili içgörüleri desteklemek için IFileContextProvider arabirimini uygulayan dosya bağlamı sağlayıcıları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 92658912e6910f21c6e79f779dff66b6c8b85a04b55f138a0971903789d4c8a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374591"
---
# <a name="workspace-file-contexts"></a>Çalışma alanı dosya bağlamları

Açık Klasör çalışma [alanlarıyla](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) ilgili tüm içgörüler, arabirimi uygulayan "dosya bağlamı sağlayıcıları" tarafından <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> üretir. Bu uzantılar, bir dosya bağlamı tanımlamak için ihtiyaçları olan içgörüleri biriktiren klasörlerde veya dosyalarda desenleri, MSBuild dosyalarını ve makefile'ları okuyabilir, paket bağımlılıklarını algılar. Dosya bağlamı tek başına herhangi bir eylem gerçekleştirmez, bunun yerine başka bir uzantının üzerinde işlem gerçekleştirecek verileri sağlar.

Her <xref:Microsoft.VisualStudio.Workspace.FileContext> `Guid` biri, taşıdığı veri türünü tanımlayan ilişkili bir veriye sahip. Çalışma alanı bunu `Guid` daha sonra özelliği aracılığıyla verileri kullanan uzantılarla eşleşmek için <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> kullanır. Dosya bağlamı sağlayıcısı, hangi dosya bağlamı için veri oluştura olduğunu `Guid` tanımlayan meta verilerle birlikte dışarı aktarıldı.

Tanımlandığı anda, bir dosya bağlamı çalışma alanında istediğiniz sayıda dosya veya klasörle ilişkilendirilebilirsiniz. Belirli bir dosya veya klasör, herhangi bir sayıda dosya bağlamıyla ilişkili olabilir. Bu çoka çok ilişkisidir.

Dosya bağlamları için en yaygın senaryolar derleme, hata ayıklama ve dil hizmetleriyle ilgilidir. Daha fazla bilgi için bu senaryolarla ilgili diğer konulara bakın.

## <a name="file-context-lifecycle"></a>Dosya bağlamı yaşam döngüsü

için yaşam `FileContext` döngüleri belirleyici değildir. Herhangi bir zamanda, bir bileşen bazı bağlam türleri kümesi için zaman uyumsuz olarak istekte olabilir. İstek bağlam türlerinin bazı alt kümelerini destekleyen sağlayıcılar sorgulanacak. Örnek, `IWorkspace` yöntemi aracılığıyla tüketici ve sağlayıcılar arasında ortadaki adam gibi <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> davranır. Tüketiciler bağlam isteğinde olabilir ve bağlama göre bazı kısa vadeli eylemlerde yer alırken, diğerleri bağlam isteğinde olabilir ve uzun süreli bir başvuruya sahip olabilir.

Dosya bağlamının zaman dışında olmasını neden olan dosyalarda değişiklikler olabilir. Sağlayıcı, tüketicilere güncelleştirmeleri bildirmek `FileContext` için üzerinde bir olay bildirilebilir. Örneğin, bazı dosyalarda derleme bağlamı sağlanıyorsa ancak disk üzerinde yapılan bir değişiklik bu bağlamı geçersiz kılınıyorsa, özgün üretici olayı çağırabilirsiniz. Daha sonra yeni bir için yeniden `FileContext` yoklamalar için başvuran tüm `FileContext` tüketiciler.

>[!NOTE]
>Tüketicilere itme modeli yoktur. Tüketicilere istekten sonra sağlayıcının yeni durumu `FileContext` bildirilecek.

## <a name="expensive-file-context-computations"></a>Pahalı dosya bağlamı hesaplamaları

Özellikle bir sağlayıcının dosyalar arasındaki ilişkiyi çözümlemesi gerekirken diskten dosya içeriklerini okumak pahalı olabilir. Örneğin, bir sağlayıcı bazı kaynak dosyanın dosya bağlamı için sorgulansa da, dosya bağlamı bir proje dosyasındaki meta verilere bağlıdır. Proje dosyasını ayrıştırmak veya projeyle birlikte MSBuild pahalıdır. Bunun yerine uzantı, çalışma alanı dizini oluşturma `IFileScanner` sırasında veri oluşturmak için bir dışarı `FileDataValue` aktarabilirsiniz. Artık dosya bağlamları sorulsa, `IFileContextProvider` bu dizine verileri hızla sorgular. Dizin oluşturma hakkında daha fazla bilgi için Çalışma alanı [dizinleme konu başlığına](workspace-indexing.md) bakın.

>[!WARNING]
>İşlem yapmak pahalı `FileContext` olabilir. Bazı kullanıcı arabirimi etkileşimleri zaman uyumlu ve yüksek hacimli `FileContext` isteklere güveniyor. Örnek olarak bir düzenleyici sekmesi açma ve **bir** Çözüm Gezgini menüsü açılır. Bu eylemler birçok derleme bağlamı türü isteğinde lar.

## <a name="file-context-related-apis"></a>Dosya bağlamıyla ilgili API'ler

- <xref:Microsoft.VisualStudio.Workspace.FileContext> verileri ve meta verileri tutar.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> ve <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> dosya bağlamını oluşturun.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> bir dosya bağlamı sağlayıcısını dışarı aktarır.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> , tüketicilerin dosya bağlamlarını almak için kullanılır.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> , Klasör Aç'ın tükettiği derleme bağlam türlerini tanımlar.

## <a name="file-context-actions"></a>Dosya bağlamı eylemleri

Bir dosyanın kendisi yalnızca bazı dosyalarda yer alan verilerdir ancak bu verileri ifade etmek ve üzerinde `FileContext` <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> eyleme geçebilirsiniz. `IFileContextAction` , kullanımında esnektir. En yaygın durumlarından ikisi, bina ve hata ayıklamadır.

## <a name="reporting-progress"></a>Raporlama ilerleme durumu

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>yöntemi `IProgress<IFileContextActionProgressUpdate>` geçirildi, ancak bağımsız değişkeni bu tür olarak kullanılmaması gerekir. `IFileContextActionProgressUpdate` boş bir arabirimdir ve bu durumda, 'nin `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` iptali `NotImplementedException` olabilir. Bunun yerine, `IFileContextAction` bağımsız değişkeni senaryo için gerektiğinde başka bir türe attırmaları gerekir.

Visual Studio tarafından sağlanan türler hakkında bilgi için ilgili senaryonun belgelerine bakın.

## <a name="file-context-action-related-apis"></a>Dosya bağlamı eylemiyle ilgili API'ler

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> bir temel alarak bazı davranışlar `FileContext` yürütür.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> , örneklerini `IFileContextAction` oluşturur.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> türünü dışarı `IWorkspaceProviderFactory<IFileContextActionProvider>` aktarıyor.

## <a name="file-watching"></a>Dosya izleme

Çalışma alanı dosya değişikliği bildirimlerini dinler ve aracılığıyla <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> sağlar. "ExcludedItems" ayarıyla eşleşen dosyalar dosya bildirimi olayları üretmez. Olaylar arasındaki eşik, bildirim basitleştirmesi ve yinelenen azaltma için kullanılır. Bir dosya değişikliğine tepki vermenizi istediğiniz zaman bu hizmete abone olmanız gerekir.

>[!TIP]
>Çalışma alanının dizin [oluşturma hizmeti varsayılan](workspace-indexing.md) olarak dosya olaylarını abone olur. Dosya eklemeleri ve değişiklikleri, ilgili `IFileScanner` olayların bu dosya için yeni veriler için çağrılmalarını sağlar. Dosya silme işlemi dizine verileri kaldırır. Dosya izleme hizmetine abone `IFileScanner` olmanıza gerek yok.

## <a name="next-steps"></a>Sonraki adımlar

* [Dizin oluşturma](workspace-indexing.md) - Çalışma alanı dizini oluşturma, çalışma alanıyla ilgili bilgileri toplar ve kalıcı olarak devam eder.
* [Çalışma alanları](workspaces.md) - Çalışma alanı kavramlarını ve ayar depolama alanını gözden geçirin.
