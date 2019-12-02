# Datastrucutre
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';
import { map, catchError, tap } from 'rxjs/operators';
@Injectable({
  providedIn: 'root'
})
export class ServiceapiService {
   localUrl = '/assets/hdp_merge_app.json';
   localmergeappupdurl = '/assets/hdp_merge_app_upd.json';
   localenvurl = '/assets/hdp_merge_env.json';
constructor(private http: HttpClient) { }
private extractData(res: Response) {
  let body = res;
  return body || {};
}

getSmartphone() {
  return this.http.get(this.localUrl);
}

getlocalmergeappupdurl() {
  return this.http.get(this.localenvurl);
}
getlocalenvurl() {
  return this.http.get(this.localmergeappupdurl);
}

getOutputs(): Observable<any> {
  return this.http.get(this.localenvurl).pipe(
    map(this.extractData));
}
}
