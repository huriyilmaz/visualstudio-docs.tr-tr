---
title: 'Nasıl |: Kod | Microsoft Docs'
description: Yerelleştirilmiş kaynaklara başvuru SharePoint GetGlobalResourceObject çağrısıyla sabit kodlu dizeleri değiştirerek kodu yerelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c65edab726fb0def889364f37f2eed41778bcfe6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084239"
---
# <a name="how-to-localize-code"></a>Nasıl olur: Kodu yerelleştirme
  Yerel olmayan kod sabit kodlu dize değerlerini kullanır. Kod dizelerini yerelleştirmek için, yerelleştirilmiş kaynaklara <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> başvurulan bir yöntem olan çağrısıyla değiştirin.

## <a name="localize-code"></a>Kodu yerelleştirme

#### <a name="to-localize-code"></a>Kodu yerelleştirmek için

1. Bu **Çözüm Gezgini** proje öğesinin kısayol menüsünü açın ve Modül **Ekle'yi**  >  **seçin.**

     Kaynak Dosyası **şablonunu** seçin.

    > [!NOTE]
    > Dağıtım Türü özelliğinin kullanılabilir olması için kaynak SharePoint bir proje öğesine ekleyin. Bu özellik bu yordamın devamlarında gereklidir.

2. Varsayılan dil kaynak dosyasına, *MyAppResources.resx* gibi *bir .resx* uzantısıyla birlikte istediğiniz adı girin.

3. 1. ve 2. adımları tekrarlayın ve her yerelleştirilmiş dil için bir tane olmak SharePoint proje öğesine ayrı kaynak dosyaları ekleyin.

     Yerelleştirilmiş her kaynak dosyası için aynı temel adı kullanın, ancak kültür kimliğini ekleyin. Örneğin, Almanca yerelleştirilmiş bir kaynağı *MyAppResources.de-DE.resx olarak anın.*

4. Her kaynak dosyasını açın ve yerelleştirilmiş dizeler ekleyin. Her dosyada aynı dize kimliklerini kullanın.

5. Her bir dosyanın sunucunun App_GlobalResources klasörüne dağıtımına neden olmak için her bir kaynak dosyasının Dağıtım Türü özelliğinin değerini **AppGlobalResource** olarak App_GlobalResources. 

6. Her dosyanın Derleme **Eylemi özelliğinin** değerini Katıştırılmış Kaynak **olarak bırakın.**

     Katıştırılmış kaynaklar projenin DLL'sine derlenmiş.

7. Kaynak uydu URL'lerini oluşturmak için projeyi oluşturun.

8. Paket **Tasarımcısı'nda** Gelişmiş **sekmesini** seçin ve ardından uydu derlemesini ekleyin.

9. Konum **kutusunda,** *\\ \<Project Item Name> de-DE* gibi bir kültür kimliği klasörünü Konum yoluna.resources.dll.

10. Çözümünüz System.Web derlemesine henüz başvurmsa, buna bir başvuru ekleyin ve kodunıza bir yönerge <xref:System.Web> ekleyin.

11. Kodunuz içinde kullanıcı arabirimi metni, hatalar ve ileti metni gibi kullanıcılara görünür olan tüm sabit kodlanmış dizeleri bulun. Aşağıdaki sözdizimini kullanarak bunları <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> yöntemine yapılan bir çağrıyla değiştirin:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Uygulamayı **derlemek ve** çalıştırmak için F5 anahtarını seçin.

13. Bu SharePoint varsayılandan görüntüleme dilini değiştirebilirsiniz.

     Yerelleştirilmiş dizeler uygulamada görünür. Yerelleştirilmiş kaynakları görüntülemek için SharePoint sunucusunda kaynak dosyasının kültürüyle eşleşen bir dil paketi yüklü olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerelleştirme SharePoint yerelleştirme](../sharepoint/localizing-sharepoint-solutions.md)
- [Nasıl: Bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md)
- [Nasıl yapabilirsiniz: ASPX işaretlemeyi yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md)
- [Nasıl: Kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)
