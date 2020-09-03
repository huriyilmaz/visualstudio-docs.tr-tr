---
title: Bir DSL 'nin VSıX dağıtımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916556"
---
# <a name="vsix-deployment-of-a-dsl"></a>Bir DSL 'nin VSıX dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kendi bilgisayarınıza veya diğer bilgisayarlara, etki alanına özgü bir dil yükleyebilirsiniz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hedef bilgisayarda zaten yüklü olmalıdır.

## <a name="installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> VSX kullanarak DSL yükleme ve kaldırma
 Bu yöntem tarafından DSL yüklendiğinde, Kullanıcı içinden bir DSL dosyası açabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ancak dosya Windows Gezgini ' nden açılamaz.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>VSıX 'i kullanarak bir DSL yüklemek için

1. Bilgisayarınızda, DSL paketi projeniz tarafından oluşturulan **. vsix** dosyasını bulun.

    1. **Çözüm Gezgini**, **DslPackage** projesine sağ tıklayın ve ardından **klasörü Windows Gezgini 'nde aç**' a tıklayın.

    2. Dosya ** \\ \* bin \\ **_projesini_bulun **. DslPackage. vsix**

2. **. Vsix** dosyasını, DSL 'yi yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

    - Hedef bilgisayarda, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] çalışma zamanında DSLs 'yi destekleyen sürümlerinden biri olmalıdır. Daha fazla bilgi için bkz. [görselleştirme Için desteklenen Visual Studio sürümleri & modelleme SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Hedef bilgisayar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **DslPackage\source.Extensions.manifest**içinde belirtilen sürümlerden birine sahip olmalıdır.

3. Hedef bilgisayarda **. vsix** dosyasına çift tıklayın.

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. Başlatın veya yeniden başlatın [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

5. DSL 'yi test etmek için kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL 'niz için tanımladığınız uzantıya sahip yeni bir dosya oluşturun.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanılarak yüklenen bir DSL 'yi kaldırmak için

1. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın.

2. **Yüklü uzantıları**genişletin.

3. DSL 'nin tanımlandığı uzantıyı seçin ve ardından **Kaldır**' a tıklayın.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı öğesinden silerek uzantıyı kaldırabilirsiniz:

   *LocalAppData* **\Microsoft\visualstudio\10.0\Extensions**
