---
title: Visual Basic Düzenle ve devam et 'de desteklenmeyen düzenlemeler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155440"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Visual Basic Düzenle ve Devam Et'de Desteklenmeyen Düzenlemeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenle ve devam et, kesme modunda program yürütmeyi durdurur, yürütülen kodda değişiklikler yapar ve yeni eklenen değişikliklerle program yürütmeyi devam ettirir. Bir sınıfın ortak yapısını etkileyen bildirime dayalı kod düzenlemeleri genellikle yasaktır, ancak bir yöntem, Özellik gövdesi veya bir sınıf içindeki özel bildirimlere yaptığınız birçok düzenleme kullanılabilir.  
  
 Desteklenmeyen bir değişiklik yapmanız gerekiyorsa, hata ayıklamayı durdurmanız, değişiklikleri yapmanız ve yeni bir hata ayıklama oturumu başlatmanız gerekir.  
  
### <a name="method-and-property-body-edits"></a><a name="BKMK_MethodandPropertyBodyEdits"></a> Yöntem ve Özellik gövdesi düzenlemeleri  
 **Statik yerel değişkenlerde desteklenmeyen değişiklikler**: yerel bir değişken ekleme veya güncelleştirme ya da bir derleme hatasına neden olacak statik yerel değişkeni kaldırma.  
  
 Genel **türlerde desteklenmeyen değişiklikler**: genel metodun veya genel yöntem gövdesindeki değişiklikler desteklenmiyor. Genel bir türün veya mevcut genel yöntemlere yapılan çağrıların örneklenmesi eklenebilir, silinebilir veya değiştirilebilir.  
  
 **Diğer desteklenmeyen değişiklikler**  
  
- Çağrı yığınında olan bir yöntemin çağırma ifadesini değiştirme.  
  
- Bir `Try...Catch` blok ekleme yönerge işaretçisi `Catch` bloğunda veya bloğunda sona erdiğinde `Finally` .  
  
- Bir bloğu kaldırma `Try...Catch` , yönerge işaretçisi bir `Catch` blok veya blok içinde olduğunda `Finally` .  
  
- `Using`Geçerli yönerge işaretçisinin çevresine bir blok ekleniyor.  
  
- `SynchLock`Geçerli yönerge işaretçisinin çevresine bir blok ekleniyor.  
  
### <a name="attribute-edits"></a><a name="BKMK_AttributeEdits"></a> Öznitelik düzenlemeleri  
 Düzenle ve devam et özelliği, özniteliklerin değiştirilmesini desteklemiyor. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Öznitelik sınıfını tanımlama, Düzenle veya silme.  
  
- Öznitelik ekleme.  
  
- Varolan bir özniteliği Düzenle veya kaldırılıyor.  
  
### <a name="class-declaration-edits"></a><a name="BKMK_ClassDeclarationEdits"></a> Sınıf bildirimi düzenlemeleri  
 Kesme modundayken, sınıf bildirimlerinde yapılan değişikliklere Düzenle ve devam et tarafından izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Var olan bir sınıfın devralmayı yeniden adlandırma, silme veya değiştirme.  
  
- Yeni bir arabirim uygulama veya bir arabirimin uygulanmasını kaldırma.  
  
- Bir sınıftaki değiştiriciler değiştiriliyor.  
  
- Durum ekleme, değiştirme veya kaldırma `ComClass` .  
  
- Herhangi bir genel sınıf bildirimini Düzenle.  
  
### <a name="class-member-declaration-edits"></a><a name="BKMK_ClassMemberDeclarationEdits"></a> Sınıf üyesi bildirimi düzenlemeleri  
 Üye bildirimlerinde yapılan değişikliklere, çoğu düzenleme ve devam etme durumunda izin verilmez. Örneğin, bir üyenin imzasını veya erişim düzeyini değiştiremezsiniz ve bu derleme hatasına neden olacaksa üyeleri tamamen kaldıramazsınız. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Kapsayan blokta aynı ada sahip bir genel veya üye değişkeni bildirerek mevcut bir üye değişkenini gölgelendirin.  
  
- Bir blok içinde yeni bir örnek bildirerek statik bir yerel değişkeni gölgeleyerek.  
  
- Bir olayın işleyicileri kaldırılıyor. Olay işleyicisi eklenmesine izin veriliyor.  
  
- Özellik veya yöntem olmadığı ve herhangi bir etkin bildirimde hiçbir oluşum olmadığından yeni bir aşırı yükleme özelliği veya yöntemi ekleme `Private` .  
  
- `WithEvents`Üye değişkenine yan tümce ekleme veya kaldırma.  
  
- Bir üyeyi silme.  
  
- Bir arabirimi uygulamayı durdurmak için bir özellik veya yöntem bildirimini değiştirme.  
  
- Genel türler kullanan herhangi bir yöntemi düzenleyebilirsiniz.  
  
- Özel olmayan bir özelliğin veya metodun imzasını veya dönüş türünü değiştirme.  
  
- Temel sınıftaki bir üyeyi geçersiz kılma veya gölgeleme.  
  
- Veya ile işaretlenmiş herhangi bir sınıfta yeni bir alan `SequentialLayout` ekleme `ExplicitLayout` .  
  
- `MustInherit` `NotOverridable` Bir yöntemin durumunu veya durumunu değiştirme.  
  
- Bir özellik veya yöntem için erişim değiştiricilerini değiştirme.  
  
- Bir alanın türünü veya salt okunurdur durumunu değiştirme.  
  
- Ortak bir alanı değiştirme.  
  
### <a name="compiler-option-edits"></a><a name="BKMK_CompilerOptionEdits"></a> Derleyici seçeneği düzenlemeleri  
 Kesme modunda Düzenle ve devam et ' i kullanırken aşağıdaki derleyici seçeneklerini değiştiremez, ekleyemez veya kaldıramazsınız:  
  
- **Option Strict**  
  
- **Seçenek açık**  
  
- **Option Compare**  
  
### <a name="constants-edits"></a><a name="BKMK_ConstantsEdits"></a> Sabitler düzenlemeleri  
 Düzenle ve devam et modundayken sabitlere yapılan değişiklikler çok sınırlıdır. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Sabit değişken ekleme veya güncelleştirme.  
  
- Bir sabitin türünü veya değerini değiştirme.  
  
- Bir sabiti kaldırma.  
  
### <a name="delegate-and-event-declaration-edits"></a><a name="BKMK_DelegateandEventDeclarationEdits"></a> Temsilci ve olay bildirimi düzenlemeleri  
 Temsilci ve olaylardaki bazı değişikliklere, kesme modunda Düzenle ve devam et izni verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Temsilci tanımını değiştirme veya silme.  
  
- Bir olayı silme.  
  
### <a name="enumeration-edits"></a><a name="BKMK_EnumerationEdits"></a> Sabit Listesi düzenlemeleri  
 Numaralandırmalara () yapılan değişikliklere `Enums` , kesme modu sırasında Düzenle ve devam et tarafından izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Bir öğesinin temel alınan türünü değiştirme `Enum` .  
  
- Üye ekleme, değiştirme veya kaldırma `Enum` .  
  
- Erişim değiştiricisini değiştirme `Enum` .  
  
### <a name="external-declarations-edits"></a><a name="BKMK_ExternalDeclarationsEdits"></a> Dış bildirim düzenlemeleri  
 Genel olarak, Düzenle ve devam et sırasında dış yöntemlerin bildirimlerini değiştiremezsiniz. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Dış bildirim ekleme veya kaldırma.  
  
- Bir dış bildirimin imzasını veya sıralama özniteliklerini değiştirme.  
  
### <a name="imports-edits"></a><a name="BKMK_ImportsEdits"></a> Düzenlemeleri içeri aktarır  
 Düzenle ve devam et kesme modundayken deyimleri ekleme, değiştirme veya kaldırma işlemine izin vermez `Imports` .  
  
### <a name="interface-definition-edits"></a><a name="BKMK_InterfaceDefinitionEdits"></a> Arabirim tanımı düzenlemeleri  
 Arabirim uygulayan Üyeler için sık sık değişiklikler yapma izni verilse de, gerçek arabirim tanımlarındaki değişikliklere genellikle Düzenle ve devam et tarafından izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Arabirim üyeleri ekleme, değiştirme veya kaldırma.  
  
- Var olan bir arabirim siliniyor.  
  
- Bir arabirimin erişim değiştiricisini değiştirme.  
  
- Arabirim devralma hiyerarşisini değiştirme.  
  
### <a name="module-declaration-edits"></a><a name="BKMK_ModuleDeclarationEdits"></a> Modül bildirimi düzenlemeleri  
 Kesme modundayken, modül bildirimlerinde yapılan değişikliklere Düzenle ve devam et tarafından izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Yeni bir modül oluşturuluyor.  
  
- Mevcut bir modülü yeniden adlandırma veya silme.  
  
- Modül için erişim değiştiricisini değiştirme.  
  
### <a name="module-member-declaration-edits"></a><a name="BKMK_ModuleMemberDeclarationEdits"></a> Modül üyesi bildirimi düzenlemeleri  
 Düzenle ve devam et ' i kullanarak, modül üyelerinde özellikler, Yöntemler ve alanlar gibi çeşitli değişiklikleri kesme modunda yapabilirsiniz. Ancak bazı değişiklikler desteklenmez. Çoğu bilinen olarak, Düzenle ve devam et, herhangi bir üyenin tür veya imzasını ekleme, silme veya değiştirme desteği sağlamaz.  
  
 Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Herhangi bir etkin bildirimde adının tekrarının olmaması dışında yeni bir üye ekleme.  
  
- Özellik veya yöntem kaldırılıyor.  
  
- Bir özellik veya metodun imzasını değiştirme.  
  
- Alan ekleme, yeniden adlandırma, taşıma veya silme.  
  
- Genel türler kullanan herhangi bir yöntemi düzenleyebilirsiniz.  
  
- Bir özellik veya yöntem için erişim değiştiricilerini değiştirme Örneğin, `Public` olarak değiştirme `Private` .  
  
- Varolan bir alanın türünü silme veya değiştirme.  
  
### <a name="nested-type-declaration-edits"></a><a name="BKMK_NestedTypeDeclarationEdits"></a> İç içe tür bildirimi düzenlemeleri  
 Düzenle ve devam et, iç içe geçmiş bir türün başka bir ad alanına veya türe taşınmasını desteklemez.  
  
### <a name="structure-declaration-edits"></a><a name="BKMK_StructureDeclarationEdits"></a> Yapı bildirimi düzenlemeleri  
 **Kesme** modundayken, yapı bildirimlerinde yapılan değişikliklere Düzenle ve devam et tarafından izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Var olan bir yapıyı yeniden adlandırma veya silme.  
  
- Yeni bir arabirim uygulama veya bir arabirimin uygulanmasını kaldırma.  
  
- Bir yapının erişim değiştiricisini değiştirme.  
  
### <a name="structure-member-declaration-edits"></a><a name="BKMK_StructureMemberDeclarationEdits"></a> Yapı üye bildirimi düzenlemeleri  
 Düzenle ve devam et ' i kullanarak, yapı üyeleri (özellikler, Yöntemler ve alanlar) için kesme modundayken çeşitli değişiklikler yapabilirsiniz. Ancak, bazı değişiklikler desteklenmez, ancak yapı üyelerinin bildirimini etkileyen çoğu özellikle değişiklik. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
- Özellik veya yöntem kaldırılıyor.  
  
- Alan ekleme veya kaldırma.  
  
- Bir özellik veya metodun imzasını değiştirme.  
  
- Genel türler kullanan herhangi bir yöntemi düzenleyebilirsiniz.  
  
- Bir özellik ya da Yöntem bildiriminin bir arabirim uygulayıp uygulamadığını değiştirme.  
  
- Bir özelliğin veya metodun erişim değiştiricilerini değiştirme (örneğin, `Public` **Private**olarak değiştirme).  
  
- Alan kaldırılıyor.  
  
- Bir alanın türünü değiştirme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Düzenle ve devam et ile kesme modunda düzenleme uygulama](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Düzenle ve Devam Et (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
