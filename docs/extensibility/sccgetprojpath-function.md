---
description: Bu işlev, kullanıcıdan yalnızca kaynak denetimi eklentisi için anlamlı olan bir dize olan bir proje yolu ister.
title: SccGetProjPath Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3a08c09e1b04cf5e5f826520efcf64ead9113be
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220709"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath işlevi
Bu işlev, kullanıcıdan yalnızca kaynak denetimi eklentisi için anlamlı olan bir dize olan bir proje yolu ister. Kullanıcı şu olduğunda çağrılır:

- Yeni bir proje oluşturma

- Var olan bir projeyi sürüm denetimine ekleme

- Var olan bir sürüm denetimi projesi bulunmaya çalışılıyor

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parametreler
 pvContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpUser

[in, out] Kullanıcı adı (NULL Sonlandırıcı dahil SCC_USER_SIZE aşmamak için)

 lpProjName

[in, out] IDE projesinin, proje çalışma alanının veya makefile 'ın adı (NULL Sonlandırıcı dahil SCC_PRJPATH_SIZE aşmamak için).

 lpLocalPath

[in, out] Projenin çalışma yolu. `bAllowChangePath`İse `TRUE` , kaynak denetimi eklentisi bu dizeyi değiştirebilir (null sonlandırıcı dahil _MAX_PATH aşmamak için).

 lpAuxProjPath

[in, out] Döndürülen proje yolu için bir arabellek (NULL Sonlandırıcı dahil SCC_PRJPATH_SIZE aşmamak için).

 bAllowChangePath

'ndaki Bu durumda `TRUE` , kaynak denetimi eklentisi dizeyi isteyebilir ve değiştirebilir `lpLocalPath` .

 pbNew

[in, out] Gelen değer yeni bir proje oluşturulup oluşturulmayacağını gösterir. Döndürülen değer bir proje oluşturma başarısını gösterir:

|Gelen|Yorum|
|--------------|--------------------|
|TRUE|Kullanıcı yeni bir proje oluşturabilir.|
|FALSE|Kullanıcı yeni bir proje oluşturmayabilir.|

|Tarafına|Yorum|
|--------------|--------------------|
|TRUE|Yeni bir proje oluşturuldu.|
|FALSE|Var olan bir proje seçildi.|

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Proje başarıyla oluşturuldu veya alındı.|
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu.|
|SCC_E_CONNECTIONFAILURE|Kaynak denetim sistemine bağlanmaya çalışırken bir sorun oluştu.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu işlevin amacı, IDE 'nin parametreleri ve parametrelerini almasına yöneliktir `lpProjName` `lpAuxProjPath` . Kaynak denetimi eklentisi bu bilgileri kullanıcıdan isterse, bu iki dizeyi IDE 'ye geri geçirir. IDE, bu dizeleri çözüm dosyasında sürdürür ve Kullanıcı bu projeyi açtığında [SccOpenProject](../extensibility/sccopenproject-function.md) 'e geçirir. Bu dizeler, eklentinin bir projeyle ilişkili bilgileri izlemesini sağlar.

 İşlev ilk kez çağrıldığında `lpAuxProjPath` boş bir dize olarak ayarlanır. `lProjName` Ayrıca boş olabilir veya kaynak denetimi eklentisinin kullanabileceği veya yoksaybileceği IDE proje adını içerebilir. İşlev başarıyla döndürüldüğünde, eklenti iki karşılık gelen dizeyi döndürür. IDE, bu dizeler hakkında herhangi bir varsayım yapmaz, kullanmaz ve kullanıcının bunları değiştirmesine izin vermez. Kullanıcı ayarları değiştirmek isterse, IDE, `SccGetProjPath` önceki zamanda aldığı değerlerle aynı değerleri geçirerek yeniden çağrı yapılır. Bu iki dize üzerinde eklenti tam denetimini sağlar.

 İçin `lpUser` , IDE bir kullanıcı adını geçirebilir veya boş bir dizeye bir işaretçi geçirebilir. Bir Kullanıcı adı varsa, kaynak denetimi eklentisi onu varsayılan olarak kullanmalıdır. Ancak, bir ad geçirilmemişse veya oturum açma adı verilen adla başarısız olursa, eklenti kullanıcıdan bir oturum açma isteği ister ve `lpUser` geçerli bir oturum açma bilgisi aldığında adı geri iletmelidir. Eklenti bu dizeyi değiştirebileceğinden, IDE her zaman bir arabellek boyutu ayırır ( `SCC_USER_LEN` + 1).

> [!NOTE]
> IDE 'nin gerçekleştirdiği ilk eylem, `SccOpenProject` işleve veya işleve bir çağrı olabilir `SccGetProjPath` . Bu nedenle, her ikisi de aynı parametreye sahiptir ve bu da `lpUser` kaynak denetimi eklentisinin kullanıcıyı her seferinde oturum açmasını sağlar. İşlevden döndürülen bir başarısızlık olduğunu gösteriyorsa, eklenti bu dizeyi geçerli bir oturum açma adıyla doldurmalıdır.

 `lpLocalPath` , kullanıcının projeyi sakladığı dizindir. Boş bir dize olabilir. Şu anda tanımlanmış bir dizin yoksa (bir Kullanıcı, kaynak denetim sisteminden bir proje indirmeye çalışırken) ve `bAllowChangePath` ise `TRUE` , kaynak denetimi eklentisi kullanıcıdan girdi isteyebilir veya kendi dizesini içine yerleştirmek için başka bir yöntem kullanabilir `lpLocalPath` . `bAllowChangePath`İse `FALSE` , eklenti dizeyi değiştirmemelidir, çünkü Kullanıcı belirtilen dizinde zaten çalışıyor.

 Kullanıcı kaynak denetimi altına yerleştirilecek yeni bir proje oluşturursa, kaynak denetimi eklentisi aslında kaynak denetimi sisteminde bu şekilde bir arada oluşturmayabilir `SccGetProjPath` . Bunun yerine, `pbNew` projenin kaynak denetimi sisteminde oluşturulup oluşturulmadığını belirten, için sıfır olmayan bir değerle dizeyi geri geçirir.

 Örneğin, Visual Studio 'daki **Yeni proje** Sihirbazı 'ndaki bir Kullanıcı, projesini kaynak denetimine eklerse, Visual Studio bu işlevi çağırır ve eklenti, kaynak denetim sisteminde Visual Studio projesini içerecek yeni bir proje oluşturmak için uygun olup olmadığını belirler. Sihirbaz tamamlanmadan önce Kullanıcı **iptal** ' i tıklarsa, proje hiçbir şekilde oluşturulmaz. Kullanıcı **Tamam**' ı tıklarsa, Visual Studio çağrıları `SccOpenProject` , geçirme `SCC_OPT_CREATEIFNEW` ve kaynak denetimli proje bu sırada oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
