# Liferay 6.2

## Get users by custom field value

	public static List<User> getUsersByCustomFieldValue(String key, String value) throws SystemException, PortalException {
        List<User> users = new ArrayList<User>();
        long companyId = ...
        long userClassNameId = ClassNameLocalServiceUtil.getClassNameId(User.class.getName());
        List<ExpandoValue> values = ExpandoValueLocalServiceUtil.getColumnValues(companyId, userClassNameId, ExpandoTableConstants.DEFAULT_TABLE_NAME, key, value, -1, -1);
        User user;
        // iterate through list of ExpandoValues and for each element try to find corresponding user object
        for (int i = 0; i < values.size(); i++) {
            long userId = values.get(i).getClassPK();
            try {
                user = UserLocalServiceUtil.getUser(userId);
                users.add(user);
            } catch (NoSuchUserException e) {
                // user with this primary key was not found in DB
                LOGGER.error(e.getMessage(), e);
            }
        }
        return users;
    }
    
- https://web.liferay.com/fr/community/wiki/-/wiki/Main/Search+for+objects+by+custom+attributes