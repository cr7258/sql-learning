
```sql
SELECT patient_id, patient_name, conditions 
FROM Patients
WHERE conditions RLIKE '^DIAB1|\\sDIAB1'
```