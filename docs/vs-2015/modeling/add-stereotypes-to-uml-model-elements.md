---
title: UML model öğelerine stereotipler ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74292329"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>UML model öğelerine stereotipler ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML model öğesine açıklama eklemek ve özelleştirilmiş özellikler sağlamak için bir stereotipi ekleyebilirsiniz. Bir model öğesine stereotip eklemek için, stereotipin bir profilde tanımlanması ve profili bir pakete ya da model öğesini içeren modele bağlamanız gerekir. Her stereotip yalnızca UML sınıfları, kullanım örnekleri veya bileşenler gibi belirli model öğesi türlerine eklenebilir.

 Örneğin, «belirtim» stereotipine sahip bir UML sınıfı tanımlamak istiyorsanız, bu paketi veya Standart profile L2 ile bağlantılı bir model içinde oluşturmanız gerekir.

 Varsayılan olarak, her model L2 ve L3 UML Standart profillerine bağlanır.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Bir profili bir modele veya pakete bağlamak için

1. **UML Model Gezgini**'ni açın. **Mimari** menüsünde **Windows**' un üzerine gelin ve **UML Model Gezgini**' ne tıklayın.

2. Bir paketi veya stereotiplerinizi profilde uygulamak istediğiniz tüm öğeleri içeren bir modeli bulun.

3. Pakete veya modele sağ tıklayın ve ardından **Özellikler**' e tıklayın.

4. **Özellikler** penceresinde, **profiller** özelliğini kullanmak istediğiniz stereotiplerin bulunduğu profiller olarak ayarlayın.

     Profilin stereotipleri artık model veya paket içindeki tüm öğelerde kullanılabilir olacaktır. Paket başka paketler içeriyorsa, stereotipleri bunlar içindeki öğelerde de kullanılabilir olacaktır.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Model öğelerine veya ilişkilerine stereotipler eklemek için

1. Diyagramda veya **UML Model Gezgini**'nde model öğesine veya ilişkiye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

    > [!NOTE]
    > Aynı stereotiplere birkaç öğe eklemek için, birkaç öğe seçebilir ve sonra bunlardan birine sağ tıklayabilirsiniz.

2. **Stereotipler** özelliğine tıklayın ve uygulamak istediğiniz stereotipleri seçin.

     Seçili stereotipler, çoğu öğe ve ilişki türü için model öğesinde «köşeli ayraç» içinde görünür.

    > [!NOTE]
    > **Stereotipler** özelliğini göremiyorsanız veya istediğiniz stereotip görünmezse, model öğesinin bir paketin içinde veya uygun profilin bağlandığı bir modelin içinde olduğunu doğrulayın.

3. Bazı Stereotipler model öğesi için ek özelliklerin değerlerini ayarlamanıza olanak sağlar. Bu özellikleri görmek için **Stereotipler** özelliğini genişletin.

### <a name="to-create-model-elements-within-a-package"></a>Bir paket içinde model öğeleri oluşturmak için

1. UML sınıf diyagramında veya **UML Model Gezgini**' nde bir paket oluşturun.

2. Aşağıdaki yollarla pakete model öğeleri ekleyin:

    - Bir UML sınıf diyagramında, bir öğe için araca tıklayın ve sonra diyagramdaki paketin içine tıklayın.

         \- veya

    - UML Model Gezgini ' nde pakete sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından bir öğe türüne tıklayın.

         \- veya

    - UML Model Gezgini ' nde, varolan bir öğeyi pakete sürükleyin.

         \- veya

    - Bir diyagramı pakete bağlayın ve sonra diyagram içinde öğeleri oluşturun.

         Bunu yapmak için diyagramın boş bir kısmına sağ tıklayıp **Özellikler**' e tıklayın. **Özellikler** penceresinde, **bağlı paketi** istediğiniz pakete ayarlayın.

         Diyagramda oluşturduğunuz tüm yeni öğeler, bu paket içinde tanımlanacaktır.

         Bunu yalnızca bazı diyagram türleriyle yapabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML genişletmek için bir profil tanımlama](../modeling/define-a-profile-to-extend-uml.md) [profilleri ve stereotiplerle modelinizi özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md)

