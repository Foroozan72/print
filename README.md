# print
/*begin
    APEX_UTIL.DOWNLOAD_PRINT_DOCUMENT(
    p_file_name => ' 1قرارداد پرسنل ',
    p_content_disposition => 'Attachment',
    p_application_id => :APP_ID,
    p_report_query_name  => 'HOKM_NEW',
    p_report_layout_name => 'HOKM_NEW_PARMIS',
    p_report_layout_type => 'rtf',
    p_document_format => 'PDF');
end;*/
------------------------------
DECLARE
V_HEMT_CLAG_LAG  NUMBER;
BEGIN
        SELECT HEMT_CLAG_LAG 
        INTO   V_HEMT_CLAG_LAG
        FROM 
        HEMTS,CLAGS
        WHERE HEMT_EMT = :P66_HLOA_HEMT_EMT
        AND     HEMT_CLAG_LAG = CLAG_LAG;

        IF  V_HEMT_CLAG_LAG=1003 THEN
            begin
                APEX_UTIL.DOWNLOAD_PRINT_DOCUMENT(
            p_file_name             => 'چاپ قرارداد',
            p_content_disposition   => 'Attachment',
            p_application_id        => :app_id,
            p_report_query_name     => 'REP_HSPRS',
            p_report_layout_name    => 'REP_HSPRS_2',
            p_report_layout_type    => 'rtf',
            p_document_format       => 'PDF');  
            end;

        ELSE
             begin
                APEX_UTIL.DOWNLOAD_PRINT_DOCUMENT(
             p_file_name             => 'چاپ قرارداد',
            p_content_disposition   => 'Attachment',
            p_application_id        => :app_id,
            p_report_query_name     => 'REP_HSPRS',
            p_report_layout_name    => 'REP_HSPRS',
            p_report_layout_type    => 'rtf',
            p_document_format       => 'PDF');
             end;



        END IF;
END;
