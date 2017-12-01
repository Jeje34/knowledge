# Apache POI

## Drop down list 

    XSSFDataValidationHelper dvHelper = new XSSFDataValidationHelper(objectSheet);
    XSSFDataValidationConstraint dvConstraint = (XSSFDataValidationConstraint)
            dvHelper.createExplicitListConstraint(new String[]{"1","2"});
    CellRangeAddressList addressList = new CellRangeAddressList(0, 100, indCol, indCol);
    XSSFDataValidation validation = (XSSFDataValidation)dvHelper.createValidation(dvConstraint, addressList);
    validation.setShowErrorBox(true);
    objectSheet.addValidationData(validation);
