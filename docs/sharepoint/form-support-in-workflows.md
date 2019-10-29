---
title: Iş akışlarında form desteği | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b064df6729b914af7758cde86b03b886fd0e5d26
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986255"
---
# <a name="form-support-in-workflows"></a>İş akışlarında form desteği
  Dört tür form, bir iş akışında kullanılabilir: ilişkilendirme, başlatma, görev ve değişiklik. Bu form türleri bir ASPX formu veya InfoPath formu temel alabilir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belirli bir form için sağladığı destek düzeyi, aşağıdaki tablolarda açıklanan çeşitli faktörlere bağlıdır. İş akışı form türleri hakkında daha fazla bilgi için bkz. [Iş akışı formlarına genel bakış](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>XML yeniden düzenlemesi
 Bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı proje öğesine bir ASPX ilişkilendirmesi veya başlatma formu eklediğinizde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışının *Elements. xml* dosyasındaki XML 'yi, ilişki veya başlatma formuna karşılık gelen özniteliği eşitlenmiş halde tutmak için otomatik olarak şunların Form adı veya dağıtım yolu güncelleştirildiğinde ya da form silindiğinde. Ancak, bir görev veya değişiklik formu gibi diğer form türlerini bir iş akışında kullandığınızda, *Elements. xml* dosyası yeniden düzenlenmiş değildir.

## <a name="form-support-in-new-visual-studio-workflows"></a>Yeni Visual Studio iş akışlarında form desteği
 Aşağıdaki tabloda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]oluşturulan iş akışlarında ASPX veya InfoPath formlarında farklı form türleri için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] desteği listelenmektedir.

|Form türü|Visual Studio 'da ASPX formuyla oluşturulan iş akışı|InfoPath formu kullanılarak Visual Studio 'da oluşturulan iş akışı|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Kaldırma|-İş akışı **Ilişkilendirme formu** öğe şablonu kullanılarak iş AKıŞıNA bir aspx ilişkilendirme formu eklenebilir.<br />-İş akışının *Elements. xml* dosyası, form eklendiğinde, yeniden adlandırıldığında veya silindiğinde veya dağıtım yolu değiştiğinde yeniden düzenlenmiş.<br />-Daha fazla bilgi için bkz. [Izlenecek yol: ilişkilendirme ve başlatma formları Ile Iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]InfoPath ilişkilendirme form şablonu yok.<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer arasında bir tümleştirme yoktur.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil.|
|Başlatmak|-İş akışı **başlatma** formu öğe şablonu KULLANıLARAK bir aspx başlatma formu iş akışına eklenebilir.<br />-İş akışının *Elements. xml* dosyası, form eklendiğinde, yeniden adlandırıldığında veya silindiğinde veya dağıtım yolu değiştiğinde yeniden düzenlenmiş.<br />-Daha fazla bilgi için bkz. [Izlenecek yol: ilişkilendirme ve başlatma formları Ile Iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]InfoPath ilişkilendirme form şablonu yok.<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer arasında bir tümleştirme yoktur.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil.|
|Görev|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]bir ASPX görev formu şablonu yok. Bir uygulama sayfası oluşturmanız ve buna kod eklemeniz gerekir.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil.<br />-Daha fazla bilgi için bkz. [Iş akışı görev formları (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]InfoPath görev formu şablonu yok.<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer arasında bir tümleştirme yoktur.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil.|
|Değişiklik|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]bir ASPX değişiklik formu şablonu yok. Bir değiştirme formu eklemek için, bir uygulama sayfası oluşturmanız ve buna kod eklemeniz gerekir.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil. Uygun şekilde el ile düzenlemeniz gerekir.<br />-Daha fazla bilgi için bkz. [Iş akışı değişiklik formları (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]InfoPath değişiklik formu şablonu yok.<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve InfoPath Designer arasında bir tümleştirme yoktur.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>İçeri aktarılan SharePoint yeniden kullanılabilir iş akışlarında form desteği
 Aşağıdaki tabloda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]içeri aktarılan SharePoint yeniden kullanılabilir iş akışlarının her birinde ASPX veya InfoPath formlarında farklı form türleri için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] desteği listelenmektedir.

|Form türü|SharePoint Designer 'dan içeri aktarılmış bir ASPX formu içeren yeniden kullanılabilir iş akışı|SharePoint Designer 'dan içeri aktarılmış bir InfoPath formu olan yeniden kullanılabilir iş akışı|
|---------------|-------------------------------------------------------------------------------| - |
|Kaldırma|-Form, iş akışının *Elements. xml* dosyasında başvurulur.<br />-İş akışının *Elements. xml* dosyası, form yeniden adlandırıldığında veya silindiğinde veya dağıtım yolu değiştiğinde yeniden düzenlenmiş.|-Form içeri aktarıldı, ancak iş akışının *Elements. xml* dosyasında başvurulmuyor.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil.|
|Başlatmak|-Forma iş akışının *Elements. xml* dosyasında iş akışı tarafından başvuruluyor.<br />-İş akışının *Elements. xml* dosyası, form yeniden adlandırıldığında veya silindiğinde veya dağıtım yolu değiştiğinde yeniden düzenlenmiş.|-Form içeri aktarıldı, ancak iş akışının *Elements. xml* dosyasında başvurulmuyor.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil. **Note:**  Bu senaryonun çalışması için kurallar ve Özellikler eklenmelidir ve değiştirilmelidir.|
|Görev|-Form, iş akışının *Elements. xml* dosyasında başvurulur.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil.|-Form içeri aktarıldı, ancak iş akışının *Elements. xml* dosyasında başvurulmuyor.<br />-İş akışının *Elements. xml* dosyası yeniden düzenlenmiş değil. **Note:**  Bu senaryonun çalışması için kurallar ve Özellikler eklenmelidir ve değiştirilmelidir.|
|Değişiklik|Yok. ASPX değişiklik formları SharePoint Designer 'da oluşturulamıyor.|Yok. InfoPath değişiklik formları, iş akışı aktarıldığında. wsp dosyasına dahil olmayan yerleşik SharePoint Server iş akışı dışında, SharePoint Designer 'da oluşturulamaz.|

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: ilişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Mevcut bir SharePoint sitesinden öğeleri içeri aktar](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
