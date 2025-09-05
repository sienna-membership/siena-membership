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
