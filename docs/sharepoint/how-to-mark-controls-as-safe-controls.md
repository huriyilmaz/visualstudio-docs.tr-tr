---
title: 'nasıl yapılır: denetimleri Kasa denetimleri olarak işaretleme | Microsoft Docs'
description: denetimleri, bir derleme eklediğinizde bir SharePoint proje öğesinin Kasa Control Entries özelliğinde veya paket tasarımcısında güvenli denetimler olarak işaretleyin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b58cc0bb61d19925faf5b719106efb625671d82383068a1bc567028a0238c6d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352909"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Nasıl yapılır: denetimleri güvenli denetim olarak Işaretleme
  güvenlik için SharePoint, betik ekleme ve web denetimlerine karşı korunan web denetimleri arasında ayrım yapar. Korumalı denetimlere veya *güvenli denetimlere* güvenilmeyen kullanıcılar erişebilir. bir derlemeyi pakete eklediğinizde bir SharePoint proje öğesinin Kasa Control Entries özelliğinde veya **paket tasarımcısında** denetimleri güvenli olarak işaretleyebilirsiniz. Daha fazla bilgi için bkz.

- [web.config dosya Ayarlar](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) [bir Web bölümü derlemesini Kasa denetimi olarak](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))değiştirme ve kaydetme.

> [!IMPORTANT]
> Bu yordamlar tanım amaçlıdır. Denetimleri yalnızca güvenli olduklarından emin olduğunuzda güvenli olarak işaretleyin.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Kasa denetim girdileri özelliğindeki Kasa denetimleri işaretleniyor

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Güvenli denetim girişleri özelliğinde denetimleri güvenli veya güvenli olmayan şekilde işaretlemek için

1. Visual Web bölümü projesiyle bir SharePoint çözümü oluşturun.

2. Web bölümüne iki denetim ekleyin: metin kutusu ve düğme. Adları sırasıyla varsayılan değerlerinde, TextBox1 ve Button1 'de bırakın.

3. Web bölümünün **Kasa denetim girdileri** özelliğine iki girdi ekleyin. bunu yapmak için, **özellikler** penceresindeki **Kasa denetim girişleri** özelliğinin yanındaki üç nokta (![mobil tasarımcı elips ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) düğmesini seçin.

     **Kasa denetim girdileri** iletişim kutusu görüntülenir.

4. **Kasa denetim girdileri** iletişim kutusunda, **üyeler** bölmesine iki güvenli denetim girdisi eklemek için **ekle** düğmesini iki kez seçin: biri düğme ve diğeri metin kutusu için.

5. ilk güvenli denetim girişini seçin ve sonra **Kasa** özelliğinin değerini, **tür adı** özelliğini **Button1** olarak ve **Kasa betik özelliğine karşı** **yanlış** **olarak değiştirin**.

     Bu adım, düğme denetimini güvenli olmayan bir denetim olarak tanımlar.

6. Listede ikinci güvenli denetim girişini seçin. **Kasa** özelliğinin değerini **doğru** olarak bırakın ve **tür adı** özelliğini **TextBox1** olarak ve **Kasa betik özelliğine karşı** **doğru** olarak ayarlayın.

     Metin kutusu denetimi artık betik eklenmesine karşı güvenli bir denetim olarak işaretlenir.

7. İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="marking-safe-controls-in-the-package-designer"></a>paket tasarımcısında Kasa denetimleri işaretleme

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Denetimleri paket tasarımcısında güvenli veya güvenli olmayan şekilde işaretlemek için

1. Visual Web bölümü projesiyle bir SharePoint çözümü oluşturun.

2. Web bölümüne iki denetim ekleyin: metin kutusu ve düğme. Adları sırasıyla varsayılan değerlerinde, TextBox1 ve Button1 'de bırakın.

     Daha sonra kullanıldığından denetimin ad alanını bir yere göz atın.

3. Menü çubuğunda   >  Projeyi derlemek için derleme **Build Solution** ' ı seçin.

4. başka bir SharePoint çözümü oluşturun.

5. **Çözüm Gezgini**' de *Package. Package* dosyası için kısayol menüsünü açın ve **Aç** ' ı seçerek **Paket Tasarımcısını** açın.

6. **Paket tasarımcısında** **Gelişmiş** sekmesini seçin.

7. **Ek derlemeler** altında, **Ekle** düğmesini seçin ve ardından listeden **mevcut derlemeyi Ekle** ' yi seçin.

8. **varolan derlemeyi ekle** iletişim kutusunda **kaynak yolu**' nun yanındaki üç nokta (![mobil tasarımcı elips ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) düğmesini seçin.

9. adım 1 ' de oluşturduğunuz SharePoint çözümünden derlemeyi seçin ve ardından **aç** düğmesini seçin.

10. Bu örnek için **dağıtım hedefi** seçeneğini GlobalAssemblyCache olarak bırakın.

     Bu adım, derlemenin sistem genel derleme önbelleği 'ne (GAC) dağıtılmasını sağlar. Derlemenin Web uygulaması (bin) klasörüne dağıtılmasını istiyorsanız bunun yerine bu seçeneği belirleyin. daha fazla bilgi için bkz. [SharePoint Foundation 'da Web Bölümleri dağıtma](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. **Kasa denetimleri** kutusunda, **yeni öğe eklemek için buraya tıklayın ' ı** seçin.

12. Aşağıdaki tablodan özellikler için değerleri girin.

    |Özellik Adı|Değer|
    |-------------------|-----------|
    |Ad Alanı|Denetim için **BdcModelProject1. VisualWebPart1** gibi tam nitelikli ad alanı.|
    |Tür adı|Button1|
    |Bütünleştirilmiş kod adı|Güçlü bir derleme adı, örneğin: Microsoft. Office. SharePoint. Cliencizsions, sürüm = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Kasa|**Kasa** onay kutusunu temizleyin.|
    |Kasa Betiğe karşı|**Kasa betikte karşı** onay kutusunu temizleyin.|

    > [!NOTE]
    > **Paket tasarımcısının** **Gelişmiş** sekmesinden eklenen derlemeler için **derleme adı** değeri bir belirteç olamaz, bu, kesin adlı bir derleme olmalıdır. Daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Başka bir güvenli denetim girişi oluşturmak için **sekme** tuşunu seçin.

14. **Yeni bir öğe eklemek için buraya tıklayın** düğmesini seçin.

15. Aşağıdaki tablodan özellikler için değerleri girin.

    |Özellik Adı|Değer|
    |-------------------|-----------|
    |Ad Alanı|Denetim için **BdcModelProject1. VisualWebPart1** gibi tam nitelikli ad alanı.|
    |Tür adı|TextBox1|
    |Bütünleştirilmiş kod adı|Güçlü bir derleme adı, örneğin: Microsoft. Office. SharePoint. Cliencizsions, sürüm = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Kasa|**Kasa** onay kutusunu seçin.|
    |Kasa Betiğe karşı|**betiğe karşı Kasa** onay kutusunu seçin.|

16. **Sekme** tuşunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
