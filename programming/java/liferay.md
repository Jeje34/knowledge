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

## Stop Javascript minifier

Put in URL as parameters :

    &js_fast_load=0&css_fast_load=0&strip=0
    
## Get user connected

    User user = (User) request.getAttribute(WebKeys.USER);
    
or
    
    User user  = (User) request.getAttribute(WebKeys.THEME_DISPLAY).getUser();
    
or

    User user = PortalUtil.getUser(request);
    
## Duplicate a page

Site Administration -> Pages -> Add new page -> Copy a page of this site

## Create a CRON

In liferay-portlet.xml, below \<portlet\> tag :

    <scheduler-entry>
        <scheduler-event-listener-class>com.fr.totaluap.tst.portlets.invoices.cron.SendEmailsImportSummaryCron</scheduler-event-listener-class>
        <trigger>
            <cron>
                <cron-trigger-value>0 0 0 1/1 * ? *</cron-trigger-value>
            </cron>
        </trigger>
    </scheduler-entry>
    
<br>
    
    public class SendEmailsImportSummaryCron implements MessageListener {
        @Override
        public void receive(Message message) throws MessageListenerException {
            // ...
        }
    }