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
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916556"
---
# <a name="vsix-deployment-of-a-dsl"></a>Bir DSL 'nin VSıX dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kendi bilgisayarınıza veya diğer bilgisayarlara, etki alanına özgü bir dil yükleyebilirsiniz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hedef bilgisayara zaten yüklenmiş olmalıdır.

## <a name="Installing"></a>VSX kullanarak DSL yükleme ve kaldırma
 Bu yöntem tarafından DSL yüklendiğinde, Kullanıcı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]içinden bir DSL dosyası açabilir, ancak dosya Windows Gezgini ' nden açılamaz.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>VSıX 'i kullanarak bir DSL yüklemek için

1. Bilgisayarınızda, DSL paketi projeniz tarafından oluşturulan **. vsix** dosyasını bulun.

    1. **Çözüm Gezgini**, **DslPackage** projesine sağ tıklayın ve ardından **klasörü Windows Gezgini 'nde aç**' a tıklayın.

    2. Dosya **bin\\\*\\** _projem_' i bulun **. DslPackage. vsix**

2. **. Vsix** dosyasını, DSL 'yi yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

    - Hedef bilgisayar, çalışma zamanında DSLs 'yi destekleyen [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sürümlerinden birine sahip olmalıdır. Daha fazla bilgi için bkz. [görselleştirme Için desteklenen Visual Studio sürümleri & modelleme SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Hedef bilgisayar, **DslPackage\source.Extensions.manifest**içinde belirtilen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümlerinden birine sahip olmalıdır.

3. Hedef bilgisayarda **. vsix** dosyasına çift tıklayın.

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]başlatın veya yeniden başlatın.

5. DSL 'yi test etmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanarak DSL 'niz için tanımladığınız uzantıya sahip yeni bir dosya oluşturun.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX kullanılarak yüklenen bir DSL 'yi kaldırmak için

1. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın.

2. **Yüklü uzantıları**genişletin.

3. DSL 'nin tanımlandığı uzantıyı seçin ve ardından **Kaldır**' a tıklayın.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı öğesinden silerek uzantıyı kaldırabilirsiniz:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
