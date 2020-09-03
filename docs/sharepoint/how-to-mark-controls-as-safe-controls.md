---
title: 'Nasıl yapılır: denetimleri güvenli denetim olarak Işaretleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd7ed13504d3d91f4239a8ea070454e1c31b1114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016265"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Nasıl yapılır: denetimleri güvenli denetim olarak Işaretleme
  Güvenlik için SharePoint, betik ekleme ve Web denetimlerine karşı korunan Web denetimleri arasında ayrım yapar. Korumalı denetimlere veya *güvenli denetimlere*güvenilmeyen kullanıcılar erişebilir. Bir derlemeyi pakete eklediğinizde bir SharePoint proje öğesinin güvenli denetim girişleri özelliğinde veya **paket tasarımcısında** denetimleri güvenli olarak işaretleyebilirsiniz. Daha fazla bilgi için bkz.

- [web.config dosya ayarları](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) , [bir Web Bölümü derlemesini güvenli denetim olarak](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))değiştirin ve kayıt edin.

> [!IMPORTANT]
> Bu yordamlar tanım amaçlıdır. Denetimleri yalnızca güvenli olduklarından emin olduğunuzda güvenli olarak işaretleyin.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Güvenli denetim girdileri özelliğindeki güvenli denetimleri işaretleme

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Güvenli denetim girişleri özelliğinde denetimleri güvenli veya güvenli olmayan şekilde işaretlemek için

1. Visual Web Bölümü projesiyle bir SharePoint çözümü oluşturun.

2. Web bölümüne iki denetim ekleyin: metin kutusu ve düğme. Adları sırasıyla varsayılan değerlerinde, TextBox1 ve Button1 'de bırakın.

3. Web bölümünün **Güvenli denetim girdileri** özelliğine iki giriş ekleyin. Bunu yapmak için, **Özellikler** penceresindeki **Güvenli denetim girişleri** özelliğinin yanındaki üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) düğmesini seçin.

     **Güvenli denetim girdileri** iletişim kutusu görüntülenir.

4. **Güvenli denetim girdileri** iletişim kutusunda, **Üyeler** bölmesine iki güvenli denetim girdisi eklemek için **Ekle** düğmesini iki kez seçin: biri düğme ve diğeri metin kutusu için.

5. İlk güvenli denetim girişini seçin ve ardından **güvenli** özelliğinin değerini, **tür adı** özelliğini **button1**olarak ve **betik özelliğine karşı güvenli** olarak **false** **olarak değiştirin**.

     Bu adım, düğme denetimini güvenli olmayan bir denetim olarak tanımlar.

6. Listede ikinci güvenli denetim girişini seçin. **Güvenli** özelliğinin değerini **doğru** olarak bırakın ve **tür adı** özelliğini **textBox1** olarak, **komut dosyası özelliğine karşılık gelen güvenli** olarak **ise true**olarak ayarlayın.

     Metin kutusu denetimi artık betik eklenmesine karşı güvenli bir denetim olarak işaretlenir.

7. İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="marking-safe-controls-in-the-package-designer"></a>Paket tasarımcısında güvenli denetimleri işaretleme

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Denetimleri paket tasarımcısında güvenli veya güvenli olmayan şekilde işaretlemek için

1. Visual Web Bölümü projesiyle bir SharePoint çözümü oluşturun.

2. Web bölümüne iki denetim ekleyin: metin kutusu ve düğme. Adları sırasıyla varsayılan değerlerinde, TextBox1 ve Button1 'de bırakın.

     Daha sonra kullanıldığından denetimin ad alanını bir yere göz atın.

3. Menü çubuğunda **Build**  >  Projeyi derlemek için derleme**Build Solution** ' ı seçin.

4. Başka bir SharePoint çözümü oluşturun.

5. **Çözüm Gezgini**' de *Package. Package* dosyası için kısayol menüsünü açın ve **Aç** ' ı seçerek **Paket Tasarımcısını**açın.

6. **Paket tasarımcısında** **Gelişmiş** sekmesini seçin.

7. **Ek derlemeler**altında, **Ekle** düğmesini seçin ve ardından listeden **mevcut derlemeyi Ekle** ' yi seçin.

8. **Varolan derlemeyi Ekle** Iletişim kutusunda **kaynak yolu**' nun yanındaki üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) düğmesini seçin.

9. Adım 1 ' de oluşturduğunuz SharePoint çözümünden derlemeyi seçin ve ardından **Aç** düğmesini seçin.

10. Bu örnek için **dağıtım hedefi** seçeneğini GlobalAssemblyCache olarak bırakın.

     Bu adım, derlemenin sistem genel derleme önbelleği 'ne (GAC) dağıtılmasını sağlar. Derlemenin Web uygulaması (bin) klasörüne dağıtılmasını istiyorsanız bunun yerine bu seçeneği belirleyin. Daha fazla bilgi için bkz. [SharePoint Foundation 'da Web bölümleri dağıtma](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. **Güvenli denetimler** kutusunda **Yeni bir öğe eklemek Için buraya tıklayın ' ı** seçin.

12. Aşağıdaki tablodan özellikler için değerleri girin.

    |Özellik Adı|Değer|
    |-------------------|-----------|
    |Ad Alanı|Denetim için **BdcModelProject1. VisualWebPart1**gibi tam nitelikli ad alanı.|
    |Tür adı|Button1|
    |Bütünleştirilmiş kod adı|Güçlü bir bütünleştirilmiş kod adı, örneğin: Microsoft. Office. SharePoint. Clientsions, sürüm = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Güven|**Güvenli** onay kutusunu temizleyin.|
    |Betiğe karşı güvenli|**Betikte karşı güvenli** kalsın onay kutusu işaretini kaldırın.|

    > [!NOTE]
    > **Paket tasarımcısının** **Gelişmiş** sekmesinden eklenen derlemeler için **derleme adı** değeri bir belirteç olamaz, bu, kesin adlı bir derleme olmalıdır. Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Başka bir güvenli denetim girişi oluşturmak için **sekme** tuşunu seçin.

14. **Yeni bir öğe eklemek için buraya tıklayın** düğmesini seçin.

15. Aşağıdaki tablodan özellikler için değerleri girin.

    |Özellik Adı|Değer|
    |-------------------|-----------|
    |Ad Alanı|Denetim için **BdcModelProject1. VisualWebPart1**gibi tam nitelikli ad alanı.|
    |Tür adı|TextBox1|
    |Bütünleştirilmiş kod adı|Güçlü bir bütünleştirilmiş kod adı, örneğin: Microsoft. Office. SharePoint. Clientsions, sürüm = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Güven|**Güvenli** onay kutusunu seçin.|
    |Betiğe karşı güvenli|**Betiğe karşı güvenli** ' i seçin onay kutusu.|

16. **Sekme** tuşunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
