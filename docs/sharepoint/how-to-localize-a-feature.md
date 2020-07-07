---
title: 'Nasıl yapılır: bir özelliği yerelleştirme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0d15654ba48b6c95cf2b2f7fa4f9cd665f0959a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016136"
---
# <a name="how-to-localize-a-feature"></a>Nasıl yapılır: bir özelliği yerelleştirme
  Varsayılan olarak, özellik başlıkları ve açıklamaları sabit kodlanmış dize değerlerini kullanır. Özellik başlığını ve açıklamasını yerelleştirmek için, dizeleri yerelleştirilmiş kaynaklara başvuran ifadelerle değiştirin.

## <a name="localize-a-feature"></a>Bir özelliği yerelleştirin

#### <a name="to-localize-a-feature"></a>Bir özelliği yerelleştirmek için

1. **Çözüm Gezgini**' de, **özellik1** düğümünün kısayol menüsünü açın ve **Özellik kaynağı Ekle**' yi seçin.

2. **Kaynak Ekle** iletişim kutusunda, varsayılan dil özelliği kaynak dosyası için kültür olarak listeden **sabit dil** ' i seçin.

3. Yerelleştirilmiş özellik kaynak dosyaları için tercih ettiğiniz dilleri seçerek, yerelleştirilmiş her dil için önceki adımı yineleyin.

     Ayrı özellik kaynak dosyaları oluşturulur: biri varsayılan dil için ve, desteklemek istediğiniz her yerelleştirilmiş dil için bir tane.

4. Kaynak düzenleyicisinde her bir kaynak dosyasını açın ve ardından tüm dize kimliklerini ve değerlerini girin.

     Örneğin, varsayılan özellik kaynak dosyasında, **özellik unvanım**değeri olan BIR **başlık** kimliği ve **özellik açıklamamın** **değeri ile ikinci** bir dize kimliği girin. Her yerelleştirilmiş kaynak dosyası için, varsayılan özellik kaynağında kullanılan dize kimliklerini kullanın, ancak değerler için yerelleştirilmiş dizeler girin.

5. Tüm kaynak değerlerini girdikten sonra, özelliğin kısayol menüsünü açın (örneğin, *özellik1. feature*) ve sonra özellik tasarımcısında özelliği açmak Için **tasarımcıyı görüntüle** ' yi seçin.

6. Özelliğindeki **başlık** ve **Açıklama** alanlarını yerelleştirmek için, kutularına değer girmek üzere aşağıdaki biçimi kullanın:

     `$Resources:`*DIZE kimliği*

     Örneğin, **özellik başlık** kutusuna $Resources:**title** yazın ve **Özellik Açıklama** kutusunda $Resources:**açıklamasını** girin.

     Dize kimlikleri, kaynak dosyalarında kullanılanlarla aynı olmalıdır.

7. Uygulamayı derlemek ve çalıştırmak için **F5** tuşunu seçin.

8. SharePoint 'te **Site eylemleri** menüsünü açın, **site ayarları**' nı seçin ve ardından **Site eylemleri** bölümünde **site özelliklerini yönet** bağlantısını seçin.

9. SharePoint 'te varsayılan değer olan görüntüleme dilini değiştirin.

     Yerelleştirilmiş özellik başlığı ve açıklaması uygulamada görüntülenir. Yerelleştirilmiş kaynakları göstermek için SharePoint sunucusunda, kaynak dosyasının kültürüyle eşleşen bir dil paketi yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md)
- [Nasıl yapılır: kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)
- [Nasıl yapılır: ASPX işaretlemesini yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md)
- [Nasıl yapılır: kod yerelleştirme](../sharepoint/how-to-localize-code.md)
