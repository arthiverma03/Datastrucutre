
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';
import { map, catchError, tap } from 'rxjs/operators';
@Injectable({
  providedIn: 'root'
})
export class ServiceapiService {
   localUrl = '/assets/ss.json';
   localmergeappupdurl = '/assets/aa.json';
   localenvurl = '/assets/aa.json';
constructor(private http: HttpClient) { }
private extractData(res: Response) {
  let body = res;
  return body || {};
}

getSmartphone() {
  return this.http.get(this.localUrl);
}

getlocalmergeappupdurl(payload) {
  console.log(payload);
  return this.http.post(this.localenvurl, {...payload});
  
}


getlocalenvurl() {
  return this.http.get(this.localmergeappupdurl);
}

getOutputs(): Observable<any> {
  return this.http.get(this.localenvurl).pipe(
    map(this.extractData));
}
}
