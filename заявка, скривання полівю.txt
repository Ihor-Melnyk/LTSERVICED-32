function onCardInitialize() {
  setVisibilityAtr();
}

function setVisibilityAtr() {
  const applicationType = EdocsApi.getAttributeValue("applicationType");
  if (applicationType.value) {
    switch (applicationType) {
      case "Роботи":
        setControlHide("objectName");
        setControlHide("inventoryNumber");
        setControlHide("periodPerformance");
        setControlHide("fullDescTypeWork");
        setControlHide("requirements");
        setControlHide("docNames");

        setControlShow("expecteDate");
        setControlHide("nameTD");
        setControlHide("techniCharacter");
        setControlHide("placeApplication");
        setControlHide("number");
        setControlHide("marking");
        setControlHide("unit");
        setControlHide("GOST_DSTU_No");
        setControlHide("addInformation");
        break;

      case "ТМЦ/Послуги":
        setControlShow("expecteDate");
        setControlShow("nameTD");
        setControlShow("techniCharacter");
        setControlShow("placeApplication");
        setControlShow("number");
        setControlShow("marking");
        setControlShow("unit");
        setControlShow("GOST_DSTU_No");
        setControlShow("addInformation");

        setControlHide("objectName");
        setControlHide("inventoryNumber");
        setControlHide("periodPerformance");
        setControlHide("fullDescTypeWork");
        setControlHide("requirements");
        setControlHide("docNames");
        break;

      default:
        break;
    }
  }
}

function setControlHide(code) {
  const control = EdocsApi.getControlProperties(code);
  control.hide = true;
  EdocsApi.setControlProperties(control);
}

function setControlShow(code) {
  const control = EdocsApi.getControlProperties(code);
  control.hide = false;
  EdocsApi.setControlProperties(control);
}
