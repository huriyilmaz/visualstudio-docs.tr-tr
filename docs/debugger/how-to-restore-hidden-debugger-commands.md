---
title: Gizli hata ayıklayıcı komutlarını geri yükleme | Microsoft Docs
description: Visual Studio gizli hata ayıklayıcı komutlarını geri yüklemeyi öğrenin. Bazı diller için varsayılan IDE ayarları, bazı hata ayıklayıcı komutlarını gizleyebilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b3ec2abaa4608272fcc93fae4e3fab03aa75589e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065520"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Nasıl Yapılır: Gizli Hata Ayıklayıcı Komutlarını Geri Yükleme
Visual Studio ayarladığınızda, birincil programlama diliniz için bir varsayılan ıde ayarları kümesi seçmeniz istenir. Bazı diller için varsayılan IDE ayarları, bazı hata ayıklayıcı komutlarını gizleyebilir.

 Varsayılan IDE ayarlarınız tarafından gizlenen bir hata ayıklayıcı özelliğini kullanmak istiyorsanız, aşağıdaki yordamı kullanarak komutu menüye geri ekleyebilirsiniz.

### <a name="to-restore-hidden-debugger-commands"></a>Gizli hata ayıklayıcı komutlarını geri yüklemek için

1. Bir proje açıkken, **Araçlar** menüsünde **Özelleştir**' e tıklayın.

2. **Özelleştir** Iletişim kutusunda **Komutlar** sekmesine tıklayın.

3. **Menü çubuğunda: açılan menüsünde** , geri yüklenen komutu Içermesini Istediğiniz **hata ayıklama** menüsünü seçin.

4. **Komut Ekle...** düğmesine tıklayın.

5. **Ekle komut** kutusunda, eklemek istediğiniz komutu seçin ve **Tamam**' ı tıklatın.

6. Başka bir komut eklemek için önceki adımı tekrarlayın.

7. Menüye komut eklemeyi bitirdiğinizde **Kapat** ' a tıklayın.

    > [!WARNING]
    > Bazı menü öğeleri yalnızca hata ayıklayıcı çalışma modu veya kesme modu gibi belirli modlarda olduğunda görüntülenir. Bu nedenle, bu adımları tamamladığınızda eklediğiniz bir öğe hemen görünür olmayabilir.

## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Özelleştirme Iletişim kutusunda kullanılamayan komutları geri yükleme
 Özellikle hiyerarşik menülerde bulunan bazı komutlar, **Özelleştir** iletişim kutusundan geri yüklenemez. Bu komutları geri yüklemek için yeni bir IDE ayarları koleksiyonu içeri aktarmanız gerekir.

#### <a name="to-import-new-ide-settings"></a>Yeni IDE ayarlarını içeri aktarmak için

1. **araçlar** menüsünde **içeri aktar ve dışarı aktar Ayarlar**' a tıklayın.

2. **Ayarlar içeri ve dışarı aktarma sihirbazı 'na hoş geldiniz** sayfasında, **seçili ortam ayarlarını içeri aktar**' a tıklayın ve ardından **ileri**' ye tıklayın.

3. **geçerli Ayarlar kaydet** sayfasında, mevcut ayarlarınızın kaydedilip edilmeyeceğini belirleyin ve ardından **ileri**' ye tıklayın.

4. **içeri aktarılacak ayarların bir koleksiyonunu seçin** sayfasında, **varsayılan Ayarlar** klasörü altında kullanmak istediğiniz komutları içeren bir geliştirme ayarları koleksiyonu seçin. hangi koleksiyonun seçeceğimizi görmüyorsanız, en çok hata ayıklayıcı komutlarını sağlayan **genel geliştirme Ayarlar** veya **Visual C++ geliştirme Ayarlar** deneyin.

5. **İleri**’ye tıklayın.

6. **İçeri aktarılacak ayarları seçin** sayfasında, **Seçenekler** altında, **hata ayıklamayı** seçtiğinizden emin olun. Bu ayarları da içeri aktarmak istemediğiniz sürece diğer onay kutularını temizleyin.

7. **Finish (Son)** düğmesine tıklayın.

8. **Içeri aktarma Tamam** sayfasında, **Ayrıntılar** altında ayarlarınızı sıfırlamayla ilişkili tüm hataları gözden geçirin.

9. **Kapat**’a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)