---
title: Abonelik Visual Studio yeni bir sözleşme aboneliğine | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: 80e3b300-f2fc-40d4-bbb2-c831a2fa5d34
ms.date: 01/18/2022
ms.topic: how-to
description: Bu makalede, yöneticilerin atanmış abonelikleri bir sözleşmeden diğerine nasıl geçirebilirsiniz?
ms.openlocfilehash: 347d0115c11fa6b99d74335610ffac29c8954188
ms.sourcegitcommit: ec474f32358861e1f62e92d8262051162f291edc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "136924092"
---
# <a name="migrate-subscriptions-from-one-agreement-to-another"></a>Abonelikleri bir sözleşmeden diğerine geçirme
Bir sözleşmenin Visual Studio abonelere atanmış abonelikler varsa ve şirketiniz yeni bir sözleşme satın aldısa, aboneleri geçerli sözleşmeden yeni sözleşmeye geçirmeniz gerekir. Bu makalede, atanan aboneliklerinizi yeni sözleşmeye taşıma açıklanmıştır.  

Abonelerinizi yeni sözleşmeye taşımıştınız, şöyle olur:
- Yeni bir abonelik GUID'si elde etme.
- Avantajları sıfırlanır. Örneğin, daha önce bir eğitim avantajı kullandılar, bu avantajın yeni bir örneğini alırlar. 
- Eski aboneliklerinde Azure bireysel kredilerini kullanıyorsa yeni bir aboneliği etkinleştirmesi ve Azure varlıklarını bu aboneliğe aktarması gerekir. 

Aboneleri yeni sözleşmeye taşıma işlemi üç adımdan oluşur:
1. Eski anlaşmadan geçerli abonelik atamalarınızı dışarı aktarın. 
2. Yeni sözleşmeye yüklemek için bir abonelik listesi hazırlayın. 
3. Upload listenizi yeni sözleşmeye ekleyin.

> [!IMPORTANT]
> Bu işlemi başlatmadan önce aşağıdaki noktalara dikkat edilmesi gerekir:
> - Kurumsal bayiniz, satın alınan aboneleri yeni sözleşmeye otomatik olarak aktarma seçeneğini seçtiyse, anlaşma gönderildikten 48-72 saat sonrasına kadar değişiklikleri görene kadar bu değişiklikleri göreyemebilirsiniz. Abonelerinizi el ile taşıma işlemine devam etmek için satıcınıza başvurun.  
> - Aboneleri yeni Azure Active Directory taşıma işlemini basitleştirmek için Azure Active Directory (Azure AD) gruplarını kullanabilirsiniz. Daha fazla bilgi için [bkz. Azure AD gruplarını kullanarak abonelik atama.](assign-azure-ad.md)

## <a name="export-your-current-subscription-assignments"></a>Geçerli abonelik atamalarınızı dışarı aktarma
Atanan aboneliklerinizi bir sözleşmeden diğerine geçirmenin ilk adımı, geçerli abonelik atamalarınızı CSV dosyası olarak dışarı aktarmadır. Abonelikler Visual Studio portalında abonelerin listesini ve atamalarıyla ilgili ayrıntıları dışarı aktarabilirsiniz. 

Bu bilgiler arasında şunlar yer alır: 
- Abone adı.
- E-posta adresi. 
- Bildirim e-posta adresi. 
- Abonelik düzeyi.
- Atanan tarih.
- Sona erme tarihi.
- Başvuru alanı.
- İndirmelerin etkin olup olmadığı.
- Ülke. 
- Dil.
- Abonelik durumu.
- Abonelik GUID'si.

Liste, yeni sözleşmeye yüklenmeye hazır olmak için kolayca Microsoft Excel csv dosyası olarak dışarı aktarıldı.

Atanan aboneliklerinizi dışarı aktarma:
1. Yönetici portalında [oturum açın.](https://manage.visualstudio.com)
2. Dışarı Aktar **sekmesini** seçin.
3. Bilgisayarınıza bir CSV dosyası indirecek. Dosyanın adı, geçerli sözleşmenizin adını ve türünü ve dosyanın oluşturulma tarihini yansıtacak.  

   > [!div class="mx-imgBorder"]
   > ![Aboneleri dışarı aktarma](_img/exporting-subscriptions/exporting-subscriptions.png "Atanan aboneliklerin listesini indirmek için Dışarı Aktar düğmesini gösteren ekran görüntüsü.")

## <a name="prepare-your-subscription-list-for-upload-to-the-new-agreement"></a>Abonelik listenizi yeni sözleşmeye yüklemek için hazırlama
Dışarı aktarılan abonelikler listenizi açmak ve ilgili verileri yeni sözleşmeye yüklemek için bir şablona taşımak için şu adımları uygulayın:
1. Abonelikler listenizi dışarı aktardıktan sonra oluşturulan dosyayı bulun ve açın. Aşağıdaki sütun adlarını ve ilişkili verilerini görüyor gerekir:
   - **Abone Adı**
   - **E-posta**
   - **Bildirim E-posta Adresi**
   - AAD Grubu 
   - **Abonelik Düzeyi**
   - Atanmış
   - Etkinleştirildi 
   - Sona Erme Tarihi (UTC)
   - **Başvuru**
   - **İndirmeler**
   - **Ülke**
   - **Dil**
   - Abonelik Durumu
   - **Abonelik GUID değeri**
   - Kullanım Durumu
 
   Dışarı aktaran CSV dosyasındaki tüm alanlar, aboneliklerinizi yeni sözleşmeye yüklemek için kullanılan dosyada gerekli değildir. Önceki listede kalın **olarak** görünen alanlar, listenizi karşıya yüklemek için kullanılan şablonda görünür. 



2. Aboneliklerinizi Excel için kullanabileceğiniz uygulama şablonunu indirin.  
   1. Yönetici portalında [oturum açın.](https://manage.visualstudio.com)
   1. Aboneleri **Yönet sekmesinde,** açılan listeden yeni sözleşmenizi seçin:
      > [!div class="mx-imgBorder"]
      > ![Anlaşma seçme](_img/migrate-subscriptions/choose-agreement.png "Yeni sözleşmeyi seçmek için açılan listeyi gösteren ekran görüntüsü.")
   1. **Ekle'yi** ve ardından Toplu **ekle'yi seçin.**
   1. Birden **Upload abone iletişim kutusu** görüntülenir.  
   1. 2. adım altında İndir **bağlantısını** seçerek şablonu indirin. 
      > [!div class="mx-imgBorder"]
      > ![Toplu şablon eklemeyi indirme](_img/migrate-subscriptions/download-template.png "İndir düğmesini gösteren ekran görüntüsü.")
   
      Şablon İndirilenler klasörünüzde görünür.  
   1. Şablonu açın.

3. Hem dışarı aktaran abone listesini hem de boş toplu ekleme şablonunu açın. Dışarı aktarıldı listesinden abonelik verilerinizi el ile kopyalayın ve şablona yapıştırın. 

    Dışarı aktaran abone listesinde sütunların sırası, şablonda yer alan siparişten farklıdır. Sütunların adları da biraz farklılık gösterir. Aşağıdaki tabloda her iki elektronik tabloda da ortak olan alanların adları yer almaktadır:

   | Listeyi dışarı aktarma                | Toplu şablon ekleme  |
   |----------------------------|--------------------|
   | Abone Adı            | Name               |
   | E-posta                      | Oturum Açma E-postası      |
   | Bildirim E-posta Adresi | Bildirim E-postası |
   | Abonelik Düzeyi         | Abonelik Düzeyi |
   | Başvuru                  | Başvuru          |
   | İndirmeler                  | İndirmeler          |
   | Ülke                    | Ülke            |
   | Dil                   | Dil           |
   | Abonelik GUID değeri          | Abonelik GUID değeri  |

   > [!IMPORTANT] 
   > Abonelik GUID sütunundaki tarihi **toplu** ekleme şablonuna kopyalamayın.  GUID'leri dahil etmek karşıya yüklemenin başarısız olmasına neden olur.

   > [!TIP]
   > Çok fazla aboneniz varsa, verileri kopyalayıp yapıştırıyorsanız klavye kısayollarını kullanmayı yararlı bulabilirsiniz. Bir sütundaki Abone Adı gibi tüm girdileri seçmek için sütundaki ilk girişi seçin (sütun başlığı değil), **Ctrl+Shift** tuşlarına basın ve ardından Aşağı ok tuşunu seçin. Bu, sütundaki tüm verileri seçer. 


4. Tüm verileriniz toplu ekleme şablonuna taşındığında şablonu kaydedin ve kapatın. Bu liste, yeni sözleşmenize yükley istediğiniz abonelik listesidir.

## <a name="upload-your-subscription-list-to-the-new-agreement"></a>Upload listenizi yeni sözleşmeye ekleme
1.  Yönetici [portalında](https://manage.visualstudio.com)birden çok **Upload iletişim kutusu** hala açıksa Gözat **düğmesini** seçin. Abonelik listenizi kaydeden konuma gidin, seçin ve ardından Aç'ı **seçin.** (İletişim kutusu açık yoksa Ekle'yi **ve ardından** Toplu **ekle'yi seçin.)**
    > [!div class="mx-imgBorder"]
    > ![Şablona göz atma](_img/migrate-subscriptions/browse-template.png "Birden çok abone iletişim kutusundaki Gözat düğmesini Upload ekran görüntüsü.")
1. Abonelik listenizin adı birden çok **abonenin Upload görünür.** Dosyayı **karşıya yüklemek** için Tamam'ı seçin. 
 
   Yönetici portalında, bir dosyanın karşıya yük olduğunu belirten bir durum iletisiyle kısa bir süre görüntü alabilirsiniz. Karşıya yükleme işlemi tamamlandıktan sonra Aboneler başarıyla **güncelleştirildi iletisiyle karşı karşıya yüklersiniz.**
Abonelerinizi eski sözleşmeden yeni sözleşmenize geçirme işlemi tamamlanmıştır.  
  > [!NOTE]
  > Abonelerinizi yeni sözleşmenize ekledikten sonra eski sözleşmeden kaldırmanız gerekir. Bunları kaldırmak, eski abonelikleriyle ilgili bildirim almalarını önler.

## <a name="resources"></a>Kaynaklar
- Abonelikleri yönetme hakkında Visual Studio için bkz. [Visual Studio desteği.](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- [Daha fazla Azure Active Directory atamak için kaynak grupları kullanma](assign-azure-ad.md)
- [Mevcut abonelikleri düzenleme](edit-license.md)
