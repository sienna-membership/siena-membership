import React from "react";
import { useState } from "react";
import { Check, Shield, Phone, Mail, MapPin, Calendar, ArrowRight, Building2, NotebookText, ClipboardList, ChevronRight, CircleDollarSign, Users2, Trophy, Quote, Sparkles } from "lucide-react";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";

const Feature = ({ icon: Icon, title, desc }: any) => (
  <div className="flex gap-4">
    <div className="shrink-0 rounded-2xl p-3 bg-muted"><Icon className="h-6 w-6" /></div>
    <div>
      <div className="font-semibold text-base">{title}</div>
      <p className="text-sm text-muted-foreground leading-relaxed">{desc}</p>
    </div>
  </div>
);

const Stat = ({ label, value }: any) => (
  <div className="text-center p-4 rounded-2xl bg-muted/40">
    <div className="text-3xl font-extrabold tracking-tight">{value}</div>
    <div className="text-sm text-muted-foreground mt-1">{label}</div>
  </div>
);

const Plan = ({ name, price, tag, bullets = [] }: any) => (
  <Card className="rounded-2xl shadow-sm hover:shadow-md transition">
    <CardHeader>
      <div className="flex items-center justify-between">
        <CardTitle className="text-xl font-bold">{name}</CardTitle>
        {tag && (
          <span className="text-xs bg-primary/10 text-primary px-2 py-1 rounded-full">{tag}</span>
        )}
      </div>
      <div className="mt-2 text-3xl font-extrabold tracking-tight">{price}</div>
      <p className="text-sm text-muted-foreground">부가세, 등록비 등 별도 / 세부 조건 협의</p>
    </CardHeader>
    <CardContent className="space-y-3">
      {bullets.map((b: string, i: number) => (
        <div className="flex items-start gap-2" key={i}>
          <Check className="h-5 w-5 mt-0.5" />
          <span className="text-sm leading-relaxed">{b}</span>
        </div>
      ))}
      <Button className="w-full mt-4 group">상담 신청 <ArrowRight className="ml-2 h-4 w-4 group-hover:translate-x-0.5 transition" /></Button>
    </CardContent>
  </Card>
);

const FAQ = [
  {
    q: "더 시에나 분양 상품은 어떤 차이가 있나요?",
    a: "개인/법인, 이용 인원(등재인원), 동반/무기명 혜택, 주중/전일, 제휴 리조트 사용 조건 등에 따라 구성과 금액이 달라집니다. 초기 분양가와 현재 프로모션 가격도 상이하니 상담으로 정확히 안내드립니다.",
  },
  {
    q: "더 시에나 서울CC의 혜택은 무엇인가요?",
    a: "무기명 4인 이용(주중 7만원/주말 8만원), 정회원 2인 주중 5만원/주말 6만원, 연 30회 할인, 풀빌라 5박 포함 등 다양한 혜택이 제공됩니다. (운영정책에 따라 변동 가능)【39†source】",
  },
  {
    q: "계약/중개 절차는 안전한가요?",
    a: "모든 거래는 표준계약서, 실소유자 확인, 위임장 검증, 대금 에스크로/법무법인 입금 등 안전 절차로 진행합니다.",
  },
  {
    q: "법인 세무 혜택도 있나요?",
    a: "네. 세금계산서 발행, 부가세/법인세 처리, 비용 계상 등 일반 가이드를 드리고 필요 시 제휴 세무사 연결이 가능합니다.",
  },
];

export default function SiennaLanding() {
  const [form, setForm] = useState({ name: "", phone: "", email: "", message: "" });
  const [submitted, setSubmitted] = useState(false);

  const onSubmit = (e: any) => {
    e.preventDefault();
    setSubmitted(true);
  };

  return (
    <div className="min-h-screen bg-gradient-to-b from-white to-slate-50 text-slate-900">
      {/* 헤더 */}
      <header className="sticky top-0 z-40 backdrop-blur supports-[backdrop-filter]:bg-white/60 border-b">
        <div className="mx-auto max-w-7xl px-4 py-3 flex items-center justify-between">
          <div className="flex items-center gap-2">
            <Sparkles className="h-6 w-6" />
            <span className="font-bold">더 시에나 그룹 분양팀장 윤도해</span>
          </div>
          <nav className="hidden md:flex items-center gap-6 text-sm">
            <a href="#plans" className="hover:opacity-80">상품/가격</a>
            <a href="#benefits" className="hover:opacity-80">혜택</a>
            <a href="#process" className="hover:opacity-80">진행절차</a>
            <a href="#news" className="hover:opacity-80">소식</a>
            <a href="#faq" className="hover:opacity-80">FAQ</a>
            <a href="#contact" className="hover:opacity-80">상담신청</a>
          </nav>
          <Button asChild className="hidden md:inline-flex"><a href="#contact">지금 상담하기</a></Button>
        </div>
      </header>

      {/* 히어로 */}
      <section className="mx-auto max-w-7xl px-4 pt-14 pb-12">
        <div className="grid md:grid-cols-2 gap-10 items-center">
          <div>
            <h1 className="text-3xl md:text-5xl font-extrabold leading-tight tracking-tight">
              더 시에나 서울CC <span className="text-primary">특별회원 모집</span>
            </h1>
            <p className="mt-4 text-base md:text-lg text-muted-foreground leading-relaxed">
              상위 0.1%가 선택한 가치 있는 휴식, 더 시에나 서울CC(구 곤지암 중부CC)는 강남에서 40분 거리에 위치한 수도권 명문 골프장입니다. 정교하게 다듬어진 18홀 프리미엄 코스를 통해 차별화된 품격을 누리실 수 있습니다.【38†source】
            </p>
            <div className="mt-6 flex flex-wrap gap-3">
              <Button size="lg">상담 신청</Button>
              <Button variant="outline" size="lg">브로셔 다운로드</Button>
            </div>
            <div className="grid grid-cols-3 gap-3 mt-8">
              <Stat label="평균 응답" value="30분 이내" />
              <Stat label="상담 만족도" value="4.9/5.0" />
              <Stat label="누적 상담" value="1,200+" />
            </div>
          </div>
          <div className="md:pl-8">
            <img src="/images/sienna-seoul-brochure.jpg" alt="더 시에나 서울CC 브로슈어" className="rounded-2xl shadow" />
          </div>
        </div>
      </section>

      {/* 갤러리 */}
      <section className="mx-auto max-w-7xl px-4 py-12">
        <h2 className="text-2xl md:text-3xl font-extrabold">갤러리</h2>
        <div className="grid md:grid-cols-3 gap-6 mt-6">
          <img src="/images/sienna-seoul-brochure.jpg" alt="서울CC" className="rounded-2xl shadow" />
          <img src="/images/sienna-veluto.jpg" alt="벨루토CC" className="rounded-2xl shadow" />
          <img src="/images/sienna-jeju.jpg" alt="제주CC" className="rounded-2xl shadow" />
          <img src="/images/sienna-lounge.jpg" alt="라운지 청담" className="rounded-2xl shadow md:col-span-3" />
        </div>
      </section>

      {/* 상품/가격 */}
      <section id="plans" className="mx-auto max-w-7xl px-4 py-12">
        <h2 className="text-2xl md:text-3xl font-extrabold">상품 & 가격</h2>
        <p className="mt-2 text-muted-foreground">아래 조건은 모집안내 기준이며 운영정책에 따라 변동될 수 있습니다.【39†source】</p>
        <div className="grid md:grid-cols-2 gap-6 mt-6">
          <Plan
            name="크라운 (창립)"
            price="20억원"
            tag="창립특가"
            bullets={[
              "무기명 4인 (주중 7만원/주말 8만원)",
              "정회원 2인 (주중 5만원/주말 6만원)",
              "연 30회 할인 적용",
              "풀빌라 5박 포함",
            ]}
          />
          <Plan
            name="헤리티지 (1차)"
            price="25억원"
            bullets={[
              "무기명 4인 (주중·주말 8만원)",
              "정회원 2인 입회 후 1년간 50% 할인",
              "연 30회 할인 적용",
              "정회원 포함 6인까지 혜택",
            ]}
          />
        </div>
      </section>

      {/* 혜택 */}
      <section id="benefits" className="mx-auto max-w-7xl px-4 py-12">
        <h2 className="text-2xl md:text-3xl font-extrabold">주요 혜택</h2>
        <div className="grid md:grid-cols-2 gap-6 mt-6">
          <Card className="rounded-2xl">
            <CardHeader><CardTitle>골프</CardTitle></CardHeader>
            <CardContent className="space-y-2 text-sm">
              <div className="flex gap-2"><Check className="h-5 w-5" /> 더 시에나 서울CC/벨루토CC/제주 체인 이용</div>
              <div className="flex gap-2"><Check className="h-5 w-5" /> 정회원/무기명 구분에 따른 할인(최대 70%)</div>
              <div className="flex gap-2"><Check className="h-5 w-5" /> 연간 이용횟수 보장 (연 30회)【39†source】</div>
            </CardContent>
          </Card>
          <Card className="rounded-2xl">
            <CardHeader><CardTitle>리조트/라운지</CardTitle></CardHeader>
            <CardContent className="space-y-2 text-sm">
              <div className="flex gap-2"><Check className="h-5 w-5" /> 더 시에나 리조트·프리모·라운지 청담 혜택</div>
              <div className="flex gap-2"><Check className="h-5 w-5" /> 식음료 20%, 주류 10% 할인 (1년 이후 적용)</div>
              <div className="flex gap-2"><Check className="h-5 w-5" /> 객실 회원가 및 레이트 체크아웃</div>
            </CardContent>
          </Card>
        </div>
      </section>

      {/* 진행 절차 */}
      <section id="process" className="mx-auto max-w-7xl px-4 py-12">
        <h2 className="text-2xl md:text-3xl font-extrabold">진행 절차</h2>
        <div className="grid md:grid-cols-4 gap-4 mt-6">
          {[
            { icon: ClipboardList, t: "상담/요건정의", d: "개인/법인, 예산, 이용패턴, 등재/무기명, 예약빈도 파악" },
            { icon: Building2, t: "상품·시세 제안", d: "분양/회원권 옵션 비교표 제공, 재고·프로모션 확인" },
            { icon: CircleDollarSign, t: "계약/검증", d: "표준계약·실소유 확인·위임장·대금 보안(에스크로/법무)" },
            { icon: Calendar, t: "이용 개시", d: "명의이전/등재, 온라인 예약 연동, 오리엔테이션" },
          ].map((s, i) => (
            <div key={i} className="p-5 rounded-2xl bg-muted/40">
              <s.icon className="h-6 w-6" />
              <div className="mt-3 font-semibold">{i + 1}. {s.t}</div>
              <div className="text-sm text-muted-foreground">{s.d}</div>
            </div>
          ))}
        </div>
      </section>

      {/* 약관 & 개인정보 */}
      <section id="terms" className="mx-auto max-w-7xl px-4 py-12">
        <h2 className="text-2xl md:text-3xl font-extrabold">이용약관 & 개인정보 처리방침</h2>
        <div className="mt-4 space-y-4 text-sm text-muted-foreground leading-relaxed">
          <p>본 사이트는 더 시에나 서울CC 특별회원 모집 관련 정보 제공을 목적으로 하며, 실제 계약 조건은 공식 계약서와 공급사 공지를 우선합니다.</p>
          <p>고객의 개인정보는 상담 및 회원 모집 관련 용도로만 사용되며, 목적 달성 후 즉시 파기합니다. 제3자 제공은 원칙적으로 없으며, 마케팅 수신 동의는 별도 선택 사항입니다.</p>
          <p>보다 자세한 사항은 별도 제공되는 이용약관 및 개인정보 처리방침 문서를 참조하시기 바랍니다.</p>
        </div>
      </section>

      {/* 푸터 */}
      <footer className="border-t">
        <div className="mx-auto max-w-7xl px-4 py-10 text-xs text-muted-foreground">
          <div className="flex flex-col md:flex-row md:items-center md:justify-between gap-4">
            <div>© {new Date().getFullYear()} 더 시에나 그룹 분양팀 · sienna-membership.kr. All rights reserved.</div>
            <div className="flex gap-4">
              <a href="#terms" className="hover:underline">개인정보 처리방침</a>
              <a href="#terms" className="hover:underline">이용약관</a>
              <a href="#terms" className="hover:underline">책임 한정/면책고지</a>
            </div>
          </div>
        </div>
      </footer>
    </div>
  );
}
