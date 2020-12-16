---
title: ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme
description: Belge düzeyi özelleştirmelerinin çeşitli yönlerini yönetmek için Office çalışma zamanının Visual Studio Araçları ServerDocument sınıfını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 585ec1842daeb4e4c4c59047383e5d53b3599bcf
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528494"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme
  `ServerDocument` [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Microsoft Office Word ve Microsoft Office Excel yüklenmemiş olsa bile belge düzeyi özelleştirmelerinin çeşitli yönlerini yönetmek için içindeki sınıfını kullanabilirsiniz. Şu görevleri gerçekleştirebilirsiniz:

- Bir belge veya çalışma kitabının veri önbelleğindeki verilere erişin ve verileri değiştirin. Daha fazla bilgi için bkz. [belgedeki önbelleğe alınmış verilerle çalışma](#CachedData).

- Bir belgeyle ilişkili özelleştirme derlemesini yönetin. Daha fazla bilgi için bkz. [belge özelleştirmesini yönetme](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>ServerDocument sınıfını anlayın
 `ServerDocument`Sınıfı, Office yüklü olmayan bilgisayarlarda kullanılmak üzere tasarlanmıştır. Bu nedenle, genellikle bu sınıfı, Office projeleri yerine konsol projeleri veya Windows Forms projeleri gibi Office ile tümleştirilebilen uygulamalarda kullanırsınız. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* derlemesinde sınıfını kullanın.

 `ServerDocument`Sınıfı kullanılarak oluşturulmuş belge düzeyi özelleştirmelerde işlem yapmak için kullanılabilir [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Office çalışma zamanı için Visual Studio 2010 araçları ve .NET Framework için Office uzantıları hakkında daha fazla bilgi için, bkz. [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Sisteminde sınıfını kullanan eski bir uygulamanız varsa `ServerDocument` `Visual Studio Tools for Office` (sürüm 3,0 çalışma zamanı), `Visual Studio Tools for Office` uygulamayı çalıştıran bilgisayarlarda sistem (sürüm 3,0 çalışma zamanı) yüklü olmalıdır. `Visual Studio 2010 Tools for Office runtime`Bu uygulamalar çalıştırılamaz.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Belgedeki önbelleğe alınmış verilerle çalışma
 `ServerDocument`Sınıfı, özelleştirilmiş belgelerde veri önbelleğiyle çalışmak için kullanabileceğiniz Üyeler sağlar. Önbelleğe alınan veriler hakkında daha fazla bilgi için bkz. sunucudaki belgelerdeki verileri [önbelleğe alma](../vsto/caching-data.md) ve [verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).

 Aşağıdaki tabloda, önbelleğe alınmış verilerle çalışmak için kullanabileceğiniz üyeler listelenmektedir.

|Görev|Kullanılacak üye|
|----------|-------------------|
|Bir belgenin veri önbelleğine sahip olup olmadığını belirleme.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>Yöntemi.|
|Bir belgedeki önbelleğe alınmış verilere erişmek için.<br /><br /> Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>Özelliği.|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Belge özelleştirmesini yönetme
 `ServerDocument`Bir belgeyle ilişkili özelleştirme derlemesini yönetmek için sınıfının üyelerini kullanabilirsiniz. Örneğin, belgenin artık özelleştirmenin bir parçası olmaması için özelleştirmeyi bir belgeden program aracılığıyla kaldırabilirsiniz.

 Aşağıdaki tabloda, özelleştirme derlemesini yönetmek için kullanabileceğiniz üyeler listelenmektedir.

|Görev|Kullanılacak üye|
|----------|-------------------|
|Belge düzeyi özelleştirmenin bir parçası olup olmadığını belirleme.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>Yöntemi.|
|Çalışma zamanında bir belgeye programlı bir şekilde özelleştirme eklemek için.<br /><br /> Daha fazla bilgi için bkz [. nasıl yapılır: belgelere yönetilen kod uzantıları iliştirme](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>Yöntemlerden biri.|
|Çalışma zamanında bir belgeden program aracılığıyla özelleştirmeyi kaldırma.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>Yöntemi.|
|Belgeyle ilişkili dağıtım bildiriminin URL 'sini almak için.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>Özelliği.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelere yönetilen kod uzantıları Iliştirme](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Önbellek verileri](../vsto/caching-data.md)
